---
name: Migrate Repo
sort: 3
---

# Migrate Repositories

To make your life easier, Gogs supports migrate repositories from other Git hosting sources through HTTP/HTTPS. To do that, you have two options, either use web interface or scriptable migration API.

## Migrate using web interface

In the URL `/repo/migrate`, you can input HTTP/HTTPS URL of a Git remote repository, along with authorization when needed. Below the source information part, you can input repository details as usual.

For example:

![](/docs/images/migrate_repo.png)

## Migrate using API

In case you have many repositories need to migrate from same of different sources, Gogs has a scriptable migration API to let you customized your migration process.

- **URL**: `/api/v1/repos/migrate`
- **Method**: `POST`
- **Parameters**:

|Parameter|Required|Note|
|---------|--------|----|
|`username`|**True**|Operator username|
|`password`|**True**|Operator password|
|`clone_addr`|**True**|Clone address (HTTP/HTTPS URL or local path)|
|`auth_username`|False|Authorization username|
|`auth_password`|False|Authorization password|
|`uid`|**True**|Repository owner ID|
|`repo_name`|**True**|Repository name|
|`mirror`|False|Submit `on` if it's a mirror|
|`private`|False|Submit `on` if it's private|
|`description`|False|Repository description|

- **Response**:
	- Success(200):
	- Failure:

	```json
	{
		"message": <error message>
	}
	```

There are also some scripts already available:

- [gogs-migrate](https://github.com/valeriangalliat/gogs-migrate)
- [BitBucket to Gogs Migration Script](https://github.com/girvo/bitbucket-to-gogs-migrator)