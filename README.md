# DB設計

## users table
デバイスを使用して作成
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|
|mail|string|null: false, unipue: true|

### Association
- has_many :groups, through: :group_users
- has_many :group_users
- has_many :massages

## groups table
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unipue: true|

### Association
- has_many :users, through: :group_users
- has_many :group_users
- has_many :messages

## messages table
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group|references|foreign_key: true|
|user|references|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## group_users table

|Column|Type|Options|
|------|----|-------|
|group|references|null: index: true, foreign_key: true, null: false|
|user|references|null: index: true, foreign_key: true, null: false|

### Association
- belongs_to :group
- belongs_to :user