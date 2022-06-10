## テーブル設計

## usersテーブル

| Column             | Type   | Options                    |
| ------------------ | ------ | -------------------------- |
| email              | string | nul: false, unique: true   |
| encrypted_password | string | null: false                |
| name               | string | null: false                |
| profile            | text   | null: false                |
| occupation         | text   | null: false                |
| position           | text   | null: false                |

## Association

- has_many :comments
- has_many :prototypes, through: :comments

## prototypesテーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| title      | string     | null: false                    | 
| catch_copy | text       | null: false                    |
| concept    | text       | null: false                    |
| user       | references | null: false, foreign_key: true |

## Association

- has_many :comments
- has_many :users, through: :comments

## commentsテーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| content   | text       | null: false                    |
| prototype | references | null: false, foreign_key: true |
| user      | references | null: false, foreign_key: true |

## Association 

- belong_to :user
- belong_to :prototype