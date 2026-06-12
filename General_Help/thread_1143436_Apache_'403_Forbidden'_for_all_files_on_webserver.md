---
title: "Apache '403 Forbidden' for all files on webserver"
date: 2009-04-29
forum: General Help
---

### Post by sdlyr8 on 2009-04-29
I just installed a fresh copy of 9.04 (instead of upgrading from my 8.04). In the process, I copied my entire /var/www/ folder and my mysql database so I could keep everything I had. I copied the database over successfully, but the www folder didn't go as well... All files that are in the root dir show up fine, along with any folders or files that I created myself. But somehow when I copied everything over, I'm guessing something happened to where they don't show up in the directory listing, and if you manually type in the URL it gives '403 Forbidden'.

ls -la gives...
> drwxrwxrwx 11 root    root      4096 2009-04-29 11:18 .
drwxr-xr-x 16 root    root      4096 2009-04-24 17:43 ..
drwxr--r--  2 stephen stephen   4096 2009-04-17 13:07 control
drwxrwxrwx  2 root    root      4096 2009-04-29 11:40 cs4320
-rwxr--r--  1 stephen stephen    918 2009-04-17 13:07 emailformat.html
drwxr--r--  2 stephen stephen   4096 2009-04-17 13:07 keller
drwxr--r--  2 stephen stephen   4096 2009-04-17 13:08 oldcrap
-rwxr--r--  1 stephen stephen     18 2009-04-17 13:07 phpinfo.php
drwxr--r-- 11 stephen stephen   4096 2009-04-17 13:08 themorningafter



and here's the tail of error.log...
> [Wed Apr 29 21:17:56 2009] [error] [client ::1] (13)Permission denied: access to /themorningafter/index.html denied
[Wed Apr 29 21:17:56 2009] [error] [client ::1] (13)Permission denied: access to /themorningafter/index.cgi denied
[Wed Apr 29 21:17:56 2009] [error] [client ::1] (13)Permission denied: access to /themorningafter/index.pl denied
[Wed Apr 29 21:17:56 2009] [error] [client ::1] (13)Permission denied: access to /themorningafter/index.php denied
[Wed Apr 29 21:17:56 2009] [error] [client ::1] (13)Permission denied: access to /themorningafter/index.xhtml denied
[Wed Apr 29 21:17:56 2009] [error] [client ::1] (13)Permission denied: access to /themorningafter/index.htm denied

Any ideas?

---

### Post by trwww on 2009-04-29
Hello,

Looks like you need a:

sudo chmod 755 themorningafter

---

### Post by sdlyr8 on 2009-04-29
Thanks! I'd swear I tried that but I guess I only THOUGHT about trying it. :-)

---

### Post by trwww on 2009-04-30
You can tell you didn't try it by the:

> **sdlyr8 said:**
> drwxr--r-- 11 stephen stephen 4096 2009-04-17 13:08 themorningafter

---

