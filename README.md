# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|strings|index: true, null:false, unique: true|
|mail|strings|null: false|


### Association
- has_many :groups,through:groups_users
- has_many :groups_user
- has_many :messages


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|strings|null :false,  unique: true|


### Association
- has_many :users,through:groups_users
- has_many :groups_users
- has_many :message


## messages
|Column|Type|Options|
|------|----|-------|
|body|text|
|images|strings|
|user_id|integer|null :false, foreign_key :true|
|group|ineteger|null :false, foreign_key :true|


### Association
- belongs_to :user
- belongs_to :group


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|


### Association
- belongs_to :group
- belongs_to :user
