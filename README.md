### acl9
---
https://github.com/be9/acl9

```
gem 'acl9', '~> 2.0'
gem 'acl9', '~> 0.12'

bin/rails g acl9:setup -h

```

```ruby
class Admin::SchoolsController < ApplicationController
  access_control do
    allow :support, :of => School
    allow :admins, :managers, :teachers, :of => :school
    deny :teachers, :only => :destroy
    action :index do
      allow anonymous, logged_in
    end
    allow logged_in, :only => :show
    deny :students
  end
  def index
  end
end

user.has_role! :admin, school
user.has_role! :admin, of: school

user.has_role! :support, School
user.has_role! :support, for: School

user.has_no_role! :support, School
user.has_no_role! :support, at: School

user.has_role! :admin, school

# config/initializers/acl9.rb
Acl9.config.default_association_name = :roles
Acl9.configure do |c|
  c.default_association_name = :roles
end

Acl9.config.reset!

user.has_role! :manager, department

user.has_role? :manager, department
user.has_role? :manager, in: department

user.has_role? :manager
user.has_role? :manager

user.has_role! 'FooBars'
user.has_role? 'FooBars'
user.has_role? :foo_bar
user.has_role! :foo_bar

Role.all.each do |role|
  role.update! name: role.name.underscore.singularize
end

allow all, actions: [ :index, :show ]
```

```ruby
subject.has_role?(role, object)

allow ROLE_LIST, OPTIONS
deny ROLE_LIST, OPTIONS








```

