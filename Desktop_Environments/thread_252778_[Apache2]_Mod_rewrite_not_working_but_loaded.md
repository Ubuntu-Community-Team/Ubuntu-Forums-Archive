---
title: "[Apache2] Mod_rewrite not working but loaded?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Xilon on 2006-09-07
I can't seem to get mod_rewrite to work at all. I'm kind of new to the way apache has changed their module etc system in 2.0 so I may be missing a step. To enable the module I just created a link from mods-available/rewrite.load to mods-enabled/rewrite.load.
[quote=phpinfo()]
Loaded Modules
core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_cgi mod_php5 **mod_rewrite** mod_userdir
[/quote]

When I try to make even the simplest rewrite rule it just doesn't work. For example
```

RewriteEngine on
RewriteRule ^/nonexistant.html$ existant.html

```
All I get is a 404 when trying to access [http://localhost/nonexistant.html](http://localhost/nonexistant.html) instead of getting existant.html

Did I not enable something? Can anyone help me getting this thing to work? :( I don't know why it doesn't work now, it has worked flawlessly in the past using Apache2

---

### Post by souki on 2006-09-07
to use "RewriteRule" you need to configure apache so that both mod_rewrite and mod_proxy is installed

you need to add "proxy.load" to the "mods-available" directory

---

### Post by Xilon on 2006-09-09
Thank you, that seemed to have worked! :)

---

### Post by gcalx on 2006-10-12
I think I'm gonna loose my mind with this. I have done all the tips on this forum and no go. Last time I had fight with this rewrite, I just compiled apache from the source. Now I'd like to get this working without compiling. Any ideas?

Edit: nevermind. I just compiled it and it works like it should. But anyway this problem feels strange cause I have tried this two times. Both on clean install (on dapper and edgy) and it's always the same problem -> php.info shows that rewrite-module is enabled but it doesn't work.

---

### Post by n0ah420 on 2006-11-25
> **gcalx said:**
> I think I'm gonna loose my mind with this. I have done all the tips on this forum and no go. Last time I had fight with this rewrite, I just compiled apache from the source. Now I'd like to get this working without compiling. Any ideas?

Edit: nevermind. I just compiled it and it works like it should. But anyway this problem feels strange cause I have tried this two times. Both on clean install (on dapper and edgy) and it's always the same problem -> php.info shows that rewrite-module is enabled but it doesn't work.

Probably the /etc/apache2/sites-enabled/000-default was causing the problem.  Usually what happens is
```
AllowOverride None
```
is set.  My opinion is the excessive splitting out of the apache2 configuration leads to more mistakes, not less.

---

### Post by dualusbibook on 2006-12-30
This post is a little old but I am not having any luck with getting mod_rewrite to work:

I have verified that it is enabled (mods-enabled, php check '<?php phpinfo(); ?>', etc).

Looking in /etc/apache2/sites-enabled/000-default I have changed both instances of AllowOverride to 'all' (they were both none).

I have tried adding:

<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>

To the apache2.conf file and the 000-default virtual host but neither worked.  I have removed this from my files.

With all the changes to my conf files I restart apache.  As that may be an obvious miss.

A test .htaccess file I have been using is:
RewriteEngine On
RewriteBase /
RewriteRule ^/test/ [http://www.google.com](http://www.google.com) [R]

(as borrowed from another post)

My goal is to eventually put in a directive that changes uses username.tld.com instead of someone typing tld.com/users/username.

Any thoughts or ideas would be appreciated.  I've been trying to get this to work for a while now.

---

### Post by Gigi33 on 2008-06-05
Since I've found this post googling for a solution to my problem I'll add what was wrong with my configuration.

Make sure your httpd.conf is right. In my case the directory block where ```
AllowOverride All
``` is set **was set to the wrong directory**, so mod_rewrite didn't work at all. After setting it to the same directory as DocumentRoot it worked fine.

Maybe it helps someone.
Cheers!

---

