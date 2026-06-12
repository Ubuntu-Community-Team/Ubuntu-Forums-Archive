---
title: "display and refresh images on framebuffer console"
date: 2010-08-20
forum: Desktop Environments
---

### Post by Tee.Gee on 2010-08-20
Hi,

I'm trying to display munin graph images on a console. The problem is I can't work out how to make them automatically refresh when they change.

I have tried
- fbi: doesn't reload when images change
- w3m image.png: doesn't reaload when images change
- w3m index.html with a http_equip refresh header: reloads but uses images from the cache
- w3m index.html with a filename image.png?xyz where xyz was replaced by javascript Date.Milliseconds() string but w3m doesn't support js
- w3m [http://host/index.html](http://host/index.html) with Header set cache-Control "max-age=0" and Header set Cache-Control "no-cache" and Header set Pragma "no-cache" in .htaccess: this works for firefox but w3m doesn't seem to care much and still displays a cached image
- w3m [http://host/index.pl:](http://host/index.pl:) couldn't work out how to generate a http_equiv refresh header with the CGI module

Now I'm out of ideas. Any suggestions?
Please don't say "install X and use firefox"

Cheers,
  Tom

---

