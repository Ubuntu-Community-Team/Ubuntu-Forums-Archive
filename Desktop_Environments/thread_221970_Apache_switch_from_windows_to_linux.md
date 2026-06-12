---
title: "Apache switch from windows to linux"
date: 2006-07-24
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-24
My friend has a small website running on Apache server ,Windows version.
She has some strange permission problems which the two of us don’t know how to solve (the browser can’t open some pix on her website due to permission issues , but we can’t figure out why because they are identical in their origin to those that the browser can view),
I advised her to run it on a Linux machine where permission problems are easier for me to solve and she agreed.
The problem is that all the pix on the html files are linked and the links are windows link (like :D/ApacheServer/Pixfile/6667.jpg) .There are quite a lot of pictures. Is there a smart way to change all the links to Linux links (like /var/www/Pixfile/6667.jpg) at once without changing each one individually ?

---

### Post by firebadger on 2006-07-24
You don't need to include the /var/www in the web pages.  Assuming your page is in /var/www your links should simply be Pixfile/6667.jpg
I may be misunderstanding you.

---

