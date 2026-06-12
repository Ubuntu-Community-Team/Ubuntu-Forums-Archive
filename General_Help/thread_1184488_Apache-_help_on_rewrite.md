---
title: "Apache- help on rewrite"
date: 2009-06-11
forum: General Help
---

### Post by Shashankj on 2009-06-11
Hi All,
 
I have apache2 on my ubuntu box. 
 
[SIZE=2]>  
[SIZE=2]root@test:/var/log/apache2# uname -a[/SIZE]
[SIZE=2]Linux test 2.6.24-23-server #1 SMP Thu Nov 27 19:19:15 UTC 2008 i686 GNU/Linux[/SIZE]
[SIZE=2]root@test:/var/log/apache2#[/SIZE] 
[/SIZE]
I want to use 'rewrite' functionality. I want to test simple rewrite rule for testing purpose.
 
I have enable mod_rewrite on box.
 
[SIZE=2]>  
[SIZE=2]root@test:/etc/apache2# a2enmod rewrite[/SIZE]
[SIZE=2]This module is already enabled![/SIZE]
[SIZE=2]root@test:/etc/apache2#[/SIZE]

[/SIZE] 
I have added following lines in /etc/apache2/apache2.conf
 
 
[SIZE=2]>  
[SIZE=2]RewriteEngine on[/SIZE]
[SIZE=2]RewriteRule ^/$ /rewrite/ [R][/SIZE]
[SIZE=2]RedirectMatch ^/$ [COLOR=blue][http://www.test.com/rewrite/](http://www.test.com/rewrite/)[/COLOR][/SIZE]
[SIZE=2]RewriteLog "/var/log/apache2/rewrite.log"[/SIZE]
[SIZE=2]RewriteLogLevel 3[/SIZE] 
[/SIZE]
 
I don't see any messages in rewrite.lg file. It's not getting redirected also. What's wrong?
 
The aim is to rewrite [COLOR=blue][http://www.test.com/](http://www.test.com/)[/COLOR] to [COLOR=blue][http://www.test.com/rewrite/](http://www.test.com/rewrite/)[/COLOR] for testing.
 
My ultimate aim is to rewrite URL's like below:
 
from [COLOR=blue][http://www.test.com/search?=mumbai](http://www.test.com/search?=mumbai) [/COLOR]to [COLOR=blue][http://mumbai.test.com](http://mumbai.test.com)[/COLOR]
 
Your help is appreciated.
 
Thanks and Regards,
Shashank

---

### Post by wubbzy on 2009-06-12
I'm in the same boat. My a2enmod says mod_rewrite is enabled, but when I try a simple RewriteRule, it doesn't work -- it returns 404 error -- and a log isn't generated either.

```
RewriteEngine On
RewriteLog "/var/log/apache2/rewrite.log"
RewriteRule ^foo.html$ bar.php [L]
```

How can I debug this?

---

### Post by wubbzy on 2009-06-12
Got it to work!

Got rid of the rewritelog directive. Doesn't work for some reason -- mangles the whole thing.

Put in 'AllowOverRides All' in httpd.conf.

---

