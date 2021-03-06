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
# event_app

## usersテーブル
|Column  |Type   |Options    |
|--------|-------|-----------|
|nickname|string |null: false|
|email   |string |null: false|
|password|string |null: false|
### Association
- has_many :groups_users
- has_many :groups, through:  :groups_users
- has_many :events


## groupsテーブル
|Column |Type  |Options    |
|-------|------|-----------|
|group  |string|null: false|
|user_id|string|null: false, foreign_key: true|
### Association
- has_many :groups_users
- has_many :users, through:  :groups_users
- has_many :messages


## groups_usersテーブル
|Column  |Type  |Options                       |
|--------|------|------------------------------|
|user_id |string|null: false, foreign_key: true|
|group_id|string|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## eventsテーブル
|Column  |Type  |Options                 |
|--------|------|------------------------|
|title   |string|                        |
|body    |text  |                        |
|user_id |string|null: false, foreign_key|
|group_id|string|null: false, foreign_key|
### Association
- belongs_to :user
- belongs_to :group