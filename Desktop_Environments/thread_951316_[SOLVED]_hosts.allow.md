---
title: "[SOLVED] hosts.allow"
date: 2008-10-18
forum: Desktop Environments
---

### Post by gishaust on 2008-10-18
hi everyone

I run a laptop with apache2 server on it. But when I unplug it from the network I can't get it to work in the browser. But as soon as I plug it in it will work. The address I use in the browser 127.0.0.1 it comes  up fine but if I goto 127.0.0.1/address it says it is not on the network but the folder does exist. How do I fix it?

gishaust.

---

### Post by gishaust on 2008-10-18
does anyone have any idea

---

### Post by imana86 on 2008-10-18
A fantastic site, and brilliant effort. A great piece of work.  ------ Billy ([Retro Jordans](http://www.2345kicks.com)).

---

### Post by the yawner on 2008-10-18
Could you give an exact example of the URL and how do you access it? I mean, do you just type it (the URL "127.0.0.1/address") on your browser address bar? And also, do you use the same URL when your laptop is plugged in on the network?

Additionally, how did you install Apache and where there any modifications on the apache config?

---

### Post by gishaust on 2008-10-18
yes you are right I do type in 127.0.0.1/foldername

when I installed it was a standard install with apt-get install

---

### Post by gishaust on 2008-10-19
Apache is not the issue.  It is a box in firefox 3 you have to press file then work offline and it works great.

---

### Post by sethvath on 2008-10-19
If you're referring to a LAMP stack with apache2 you shouldnt need to click on "work offline" in firefox to access localhost. Check your hosts file that 127.0.0.1 is mapped to "localhost" and try typing [http://localhost/folder](http://localhost/folder) in firefox instead

---

