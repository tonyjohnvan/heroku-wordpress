# WordPress on Heroku
This project can help you directly deploy a newer version of WordPress on Heroku environment. It also has the Woocommerce plugin installed as well, which is the biggest open source e-commerce CMS over the world. 

This repo uses latest version of WordPress and the minimal configuration needed to get everything up online on Heroku in 3 minutes! 

*as for now this repo uses WordPress 4.7.2 and Woocommerce 2.6.13*

## 3 Minutes Installation
**Just open the terminal and you're ready to go!**
#### Step 1: Clone this repo to your local:
```
git clone https://github.com/tonyjohnvan/heroku-wordpress.git
cd heroku-wordpress
```
#### Step 2: Run this command to generate the composer.lock:
```
composer update --ignore-platform-reqs
```
#### Step 3: Run this commands to prepare the heroku server:
```
heroku login
```
after entering your email address and password, you may proceed with:
```
heroku create
heroku addons:add cleardb
heroku addons:add sendgrid
```
#### Step 4: Run this commands to setup heroku server environment vars 
it's much safer than just write them in your code, and you can use [this WordPress Official API](https://api.wordpress.org/secret-key/1.1/salt/) to generate the values
```
heroku config:set AUTH_KEY = 'REPLEACE_WITH_YOURS'
heroku config:set SECURE_AUTH_KEY = 'REPLEACE_WITH_YOURS'
heroku config:set LOGGED_IN_KEY = 'REPLEACE_WITH_YOURS'
heroku config:set NONCE_KEY = 'REPLEACE_WITH_YOURS'
heroku config:set AUTH_SALT = 'REPLEACE_WITH_YOURS'
heroku config:set SECURE_AUTH_SALT = 'REPLEACE_WITH_YOURS'
heroku config:set LOGGED_IN_SALT = 'REPLEACE_WITH_YOURS'
heroku config:set NONCE_SALT = 'REPLEACE_WITH_YOURS'
```
#### Step 5: **Final step** - Deploy the Application!
```
git add .
git commit -am "initial push"
git push heroku master
heroku open
```

**ps: if you don't like the free CLEARDB that heroku had, you can update it wih any MySQLDB service, just set the environment var by:**
```
heroku config:set DATABASE_URL='mysql://USERNAME:PASSWORD@DB_HOST_NAME/DB_NAME'
```
**and heroku and wordpress will take care of it.**

## Add Plugins and Themes

if you wish to add more themes and plugins to your wordpress service, remember it **cannot** be added through the plugin search within the wordpress, **you have to add it manually** in your wordpress file system and push it to heroku:

just unzip the downloaded plugins and themes and copy it to the wordpress folder

+ for the plugins, just copy them to `wp-content/plugins` directory
+ for the themes, just copy them to `wp-content/themes` directory, **note** a Theme named Test should be in `wp-content/themes/test`. Your Theme may provide this directory as part of the archive.

then commit and push the modifications in terminal
```
git add .
git commit -am "adding themes and plugins"
git push heroku master
heroku open
```

Then go to your WordPress server and you'll see the plugins and theme waiting to be activated in the admin panel.


**Feel Free to Star if this really helps you  =)**
