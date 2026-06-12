---
title: "Apache2 Question"
date: 2006-02-16
forum: Desktop Environments
---

### Post by GoodPanos on 2006-02-16
I need some help on an issue that I'm really lost.  I want to protect a directory in /var/www/catalog/admin so that when one views any web pages in that directory a dialog pops up for user and password.  I want to accomplish this by using a .htaccess file.

Any help is greatly appreciated.

---

### Post by heimo on 2006-02-16
This is the best place to check how it works:
[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

AllowOverride must include Authconfig (this needs to be in site specific configuration file, /etc/apache2/sites-enabled/something, inside Directory section), you need to create .htaccess file and password file (using htpasswd).

---

### Post by GoodPanos on 2006-02-17
Thank you for the response.  I'm still confused though.

Which file does the *AllowOverride AuthConfig* directive go and under what section?  In /etc/apache2/sites-enabled there is a file called *000-default*.  Is that where I should put the directive?

What goes in the .htaccess file?  I got the password creation part.

---

### Post by heimo on 2006-02-17
I don't have default Apache configuration handy, but you should have at least some Directory-sections in there. That's where you can place AllowOverride directive. Then you need to restart / reload Apache.
It's a good idea to check that configuration files syntax is ok, using
```
apache2ctl configtest
sudo /etc/init.d/apache2 restart
```

In .htaccess file you can put something like:
```
AuthName "restricted directory"
AuthType Basic
AuthUserFile /etc/apache2/passwd
require valid-user

```

AuthUserFile is the file you create using something like:
```
htpasswd -c /etc/apache2/passwd newusername
```

---

### Post by GoodPanos on 2006-02-18
I put *AllowOverride AuthConfig* directive into /etc/apache2/sites-available/default but it would give me an error.  Then I changed *AllowOverride* to Options and it would just let me straight into the website.  Finally I changed it to **All** and this time I would get a Forbidden message that I did not have access to the website.:confused: 

I also created another <Directory> in the default file specifically for the folder I wanted to protect and I got the same results.

Finally I gave up and put all the .htaccess directives in a <Directory...> in the default configuration file and that worked fine.:-k 

I do though would prefer to use an .htaccess file.

In .htaccess file do all the directives have to be between a <Directory></Directory>?

---

