---
title: "Apache2 configuration problem"
date: 2009-04-29
forum: General Help
---

### Post by nruner on 2009-04-29
I installed LAMP on an ubuntu server, the default directory for web pags is /var/www, I put some of html and php files in /var/www, they can be opened correctly in a web browser if I tylped "http://localhost". 

Now there are some other web pages in /home/mysite/, I hope the web pages can be opened in web browser too if I type in "http://localhost/mysite", I don't know how to do it, changing DocumentRoot to /home doesn't work.  Who could give some detailed examples? Thanks!

---

### Post by nruner on 2009-04-30
Any help?

---

### Post by mb_webguy on 2009-04-30
If you're setting up an actual web server to host a website, you *don't* want to put web files in your home directory.  The default web directory is in the root-owned /var/www for good reason.  

If this is a development server, however, for greater convenience you can simply edit the /etc/apache2/sites-available/default file to point to the mysite directory instead of the /var/www directory.  Or if you already have files in /var/www that you want to keep, create a www directory in your home directory, put those files and the new mysite directory inside that, and then have the /etc/apache2/sites-available/default point to your ~/www directory.

---

### Post by Bark on 2009-04-30
> **nruner said:**
> I installed LAMP on an ubuntu server, the default directory for web pags is /var/www, I put some of html and php files in /var/www, they can be opened correctly in a web browser if I tylped "http://localhost". 

Now there are some other web pages in /home/mysite/, I hope the web pages can be opened in web browser too if I type in "http://localhost/mysite", I don't know how to do it, changing DocumentRoot to /home doesn't work.  Who could give some detailed examples? Thanks!

```
Alias /mysite/  /home/mysite/
```

---

