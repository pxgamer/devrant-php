# devrant-php

A simple PHP wrapper for utilising the [devRant](https://devrant.io) api.

## Usage

__Include the class:__
- Using Composer  
`composer require pxgamer/devrant-php`  
```php
<?php
require 'vendor/autoload.php';
```
- Including the file manually  
```php
<?php
include 'src/devRant.php';
```

Once included, you can initialise the class using either of the following:
```php
$devRant = new \pxgamer\devRant();
```
```php
use \pxgamer\devRant;
$devRant = new devRant();
```

## Function Calls

Function Name         | Parameters | Returns
--------------------- | ---------- | -------
__construct()         | boolean    | `class object`
getRants()            | void       | `string (json)` or `object`
getRantById($id)      | int        | `string (json)` or `object`
getUserById($id)      | int        | `string (json)` or `object`
searchRants($query)   | string     | `string (json)` or `object`
getUsersId($username) | string     | `string (json)` or `object`
postSignIn($username, $password) | strings     | `string (json)` or `object`
postNewRant($rant_content, $user_id, $token_id, $token_key, $tags) | strings | `string (json)` or `object`

## Examples

### _Getting array of rants_
```php
$devRant = new \pxgamer\devRant();
$devRant->getRants();
```
```json
{
    "success": true,
    "rants": [
    ]
}
```

### _Getting a single rant by it's id_
```php
$devRant = new \pxgamer\devRant();
$devRant->getRantById(int);
```
```json
{
    "rant": {
    },
    "comments": [
    ],
    "success": true
}
```

### _Getting a user by their id_
```php
$devRant = new \pxgamer\devRant();
$devRant->getUserById(int);
```
```json
{
    "success": true,
    "profile": {
        "username": "",
        "score": 0,
        "about": "",
        "location": "",
        "created_time": 1474613872,
        "skills": "",
        "github": "",
        "website": "",
        "content": {
            "content": {
                "rants": [],
                "upvoted": [],
                "comments": [],
                "favorites": []
            },
            "counts": {}
        },
        "avatar": {}
    }
}
```

### _Search rants_
```php
$devRant = new \pxgamer\devRant();
$devRant->searchRants('string');
```
```json
{
    "success": true,
    "results": [
        {
            "id": 0,
            "text": "string",
            "num_upvotes": 0,
            "num_downvotes": 0,
            "score": 0,
            "created_time": 0,
            "attached_image": {
                "url": "string",
                "width": 0,
                "height": 0
            },
            "num_comments": 0,
            "tags": [
                "string"
            ],
            "vote_state": 0,
            "edited": false,
            "user_id": 0,
            "user_username": "string",
            "user_score": 0,
            "user_avatar": {
                "b": "string"
            }
        }
    ]
}
```

### _Getting a user's id from their username_
```php
$devRant = new \pxgamer\devRant();
$devRant->getUsersId('string');
```
```json
{
    "success": true,
    "user_id": 0
}
```

### _Getting signed in_
```php
$devRant = new \pxgamer\devRant();
$devRant->postSignIn('username', 'password');
```
```json
{
    "success": true,
    "auth_token": {
        "id": 18318,
        "key": "Njykalfo2143xzJt2Jux$DHsapCErDF7W291nfatd",
        "expire_time": 1484832373,
        "user_id": 1
    }
}
```

### _Posting a rant_
```php
$devRant = new \pxgamer\devRant();
$devRant->postNewRant($rant_content, $user_id, $token_id, $token_key, $tags);
```
```json
{
    "success": true,
    "rant_id": 31131
}
```
