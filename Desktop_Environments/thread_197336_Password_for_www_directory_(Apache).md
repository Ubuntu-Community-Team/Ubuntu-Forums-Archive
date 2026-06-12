---
title: "Password for www directory (Apache)"
date: 2006-06-15
forum: Desktop Environments
---

### Post by JohanSwe on 2006-06-15
I have installed Apache in synaptic on my desktop computer. Now I'm trying to set a password for the whole www directory.

I have added this to apache2.conf:
<Directory /var/www>
AllowOverride All
</Directory>
I don't know what this is for but I have read it in a howto I found.

And I have created .htaccess and .htpasswd in the directory www:

```
AuthType Basic
AuthName "Log in"
AuthUserFile /var/www/.htpasswd
require valid-user
```
```
user:password
```

But when I go to the server in firefox the files and the directories are not password protected. 

Do you have any :idea: what I'm doing #-o?

---

### Post by ifokkema on 2006-06-15
[QUOTE=JohanSwe]I have added this to apache2.conf:
<Directory /var/www>
AllowOverride All
</Directory>
I don't know what this is for but I have read it in a howto I found.[/QUOTE]
It allows your .htaccess to override all Apache settings it can. You can normally restrict the use of .htaccess files by allowing them to override only a few setting types.

[QUOTE=JohanSwe]And I have created .htaccess and .htpasswd in the directory www:

```
AuthType Basic
AuthName "Log in"
AuthUserFile /var/www/.htpasswd
require valid-user
```
```
user:password
```

But when I go to the server in firefox the files and the directories are not password protected. 

Do you have any :idea: what I'm doing #-o?[/QUOTE]

It doesn't work that way. You can't just manually create and edit a .htpasswd file. Please read this page:

[http://httpd.apache.org/docs/1.3/howto/auth.html#basicworks](http://httpd.apache.org/docs/1.3/howto/auth.html#basicworks)

You'll have it up and running in a few minutes. Good luck setting it up!

---

### Post by JohanSwe on 2006-06-19
Thanks. My .htpasswd file was with an encrypted password from the beginning. Now I also followed the guide and let apache create the file. But it still doesn't work.

I thought that it could be because of permissions so I edited the file permissions to read, write and run for everyone on both .htpasswd and .htaccess. I don't know what permissions apache has but this should work anyway. But no.

Any ideas? Anyone who have manage to get this to work on dapper?

---

### Post by ifokkema on 2006-06-20
[QUOTE=JohanSwe]Thanks. My .htpasswd file was with an encrypted password from the beginning. Now I also followed the guide and let apache create the file. But it still doesn't work.

I thought that it could be because of permissions so I edited the file permissions to read, write and run for everyone on both .htpasswd and .htaccess. I don't know what permissions apache has but this should work anyway. But no.

Any ideas? Anyone who have manage to get this to work on dapper?[/QUOTE]

I just tested this for you on a dapper install with apache 2. It works just fine. So lets go through the steps:
- I created a .htaccess page with these contents (taken from apache.org):
```
AuthType Basic
AuthName "By Invitation Only"
AuthUserFile /var/www/.htpasswd
Require valid-user
```

- I created a .htpasswd file:
```
sudo htpasswd -c ./.htpasswd asdf
```

- I changed the config file (I edited a different file than you!)
```
sudo gedit /etc/apache2/sites-available/default

```Changed:
```
AllowOverride None
```
Into:
```
AllowOverride AuthConfig
```

- Restarting Apache:
```
sudo /etc/init.d/apache2 restart
```

And it works with me...

Hope this helps!

Ivo

---

