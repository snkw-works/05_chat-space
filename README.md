# DB設計

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null:false, unique: true|
|body|text||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null:false, unique: true|
|name|string|null:false|

### Association
- has_many :users, through: :users_groups
- has_many :messages
- has_many :users_groups


## users_groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null:false, unique: true|
|user_id|references|null:false, foreign_key: true|
|group_id|references|null:false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null:false, unique: true|
|name|string|null:false|
|email|string|null:false,unique:true|
|password|string|null:false|

### Association
- has_many :groups, through: :users_groups
- has_many :users_groups
- has_many :messages
