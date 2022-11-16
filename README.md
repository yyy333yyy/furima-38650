# テーブル設計


## users テーブル

| Column             | Type        | Options                   |
| ------------------ | ----------- | ------------------------- |
| nickname           | string      | null: false               |
| email              | string      | null: false, unique: true |
| encrypted_password | string      | null: false               |
| last_name          | string      | null: false               |
| first_name         | string      | null: false               |
| lastname_kana      | string      | null: false               |
| firstname_kana     | string      | null: false               |
| birthday           | date        | null: false               |
| item               | references  | foreign_key: true         |
| purchase           | references  | foreign_key: true         |


### アソシエーション

- has_many :items
- has_many :purchases


## items テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| item_name          | string     | null: false                    |
| content            | text       | null: false                    |
| category           | string     | null: false                    |
| condition          | string     | null: false                    |
| price              | integer    | null: false                    |
| delivery_charge    | string     | null: false                    |
| delivery_from      | string     | null: false                    |
| delivery_time      | string     | null: false                    |
| image              | text       | null: false                    |
| user               | references | null: false, foreign_key: true |
| purchase           | references | foreign_key: true              |



### アソシエーション

- belongs_to :user
- has_one :purchase


## purchases テーブル

| Column             | Type        | Options                        |
| ------------------ | ----------- | ------------------------------ |
| post_code          | integer     | null: false                    |
| prefectures        | string      | null: false                    |
| municipalities     | string      | null: false                    |
| address            | string      | null: false                    |
| building           | string      |                                |
| phone_number       | integer     | null: false, unique: true      |
| user               | references  | foreign_key: true              |
| item               | references  | null: false, foreign_key: true |



### アソシエーション

- belongs_to :item
- belongs_to :user


