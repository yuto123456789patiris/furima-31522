## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| name               | string              | null: false             |
| email              | string              | null: false             |
| password           | string              | null: false             |

## Association
- has/many :items, dependent: :destroy
- has_many :comments, dependent: :destroy
- has_many :favorites, dependent: :destroy
- has_one :profile, dependent: :destroy
- has_one :sns_authentication,dependent: :destroy
- has_one :sending_destination, dependent: :destroy
- has_one :credit_card, dependent: :destroy
## profiles table

| Column | Type | Options |
|------|----|-------|
| first_name | string | null:false |
| last_name | string | null:false |
| birth_day | date | null:false |
| introduction | text |
| user | reference | null:false,foreign_key:true |


### Association
- belongs_to :user
## sending_destinations table

| Column | Type | Options |
|------|----|-------|
| destination_first_name | string | null:false |
| destination_last_name | string | null:false |
| post_code | integer | null:false |
| prefecture_code | integer | null:false |
| city | string | null:false |
| house_number | string | null:false |
| building_name | string |
| phone_number | integer | null:false |
| user | references | null:false,foreign_key:true |
（ここに追記していく）


### Association
- belongs_to: user

## credit_cards table
| Column | Type | Options |
|--------|------|---------|
| user_id | integer | null:false |
| customer_id | string | null:false |
| card_id | string | null:false |

### Association
- belongs_to: user

## items table

| Column | Type | Options |
|------|----|-------|
| name | string | null:false |
| introduction | text | null:false |
| price | integer | null:false | 
| brand | text | null:false |
| item_condition | integer | null:false,foreign_key:true |
| postage_payer | integer | null:false,foreign_key:true |
| prefecture_code | integer | null:false |
| preparation_day | integer | null:false,foreign_key: true |
| category | references | null:false,foreign_key:true |
| trading_status | integer |
| seller | references | null:false,foreign_key:true |
| buyer | references | foreign_key:true |

### Association
- has_many :comments, dependent: :destroy
- has_many :favorites, dependent: :destroy
- has_many :item_images, dependent: :destroy
- belongs_to :category
- belongs_to :user

## image table

| Column | Type | Options |
|------|----|-------|
| url | string | null:false |
| item |references | null:false,foreign_key:true |


### Association
- belongs_to :item

## comments table

| Column | Type | Options |
|------|----|-------|
| comment | text | null:false |
| user | references | null:false,foreign_key:true |
| item | references | null:false,foreign_key:true |


### Association
- belongs_to :user
- belongs_to :item

## categories table

| Column | Type | Options |
|------|----|-------|
| name | string | null:false |
| system | string | null:false |


### Association
- has_many :items