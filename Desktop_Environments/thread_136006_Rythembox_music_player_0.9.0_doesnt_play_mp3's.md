---
title: "Rythembox music player 0.9.0 doesnt play mp3's"
date: 2006-02-25
forum: Desktop Environments
---

### Post by madman0011 on 2006-02-25
I am new to linux and i havent been able to get mp3's to work. could someone help me

---

### Post by heimo on 2006-02-25
You could start over here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by sharke on 2006-02-25
Also take a look here [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)
Regards
Sharke

---

### Post by madman0011 on 2006-02-25
this is wat comes up:


patrick@ubuntu:~$ sudo apt-get install  gstreamer0.8-mad
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-mad

 then i tried replacing the 8 with a 9 cause i dot 0.9.0 and this came up

patrick@ubuntu:~$ sudo apt-get install  gstreamer0.9-mad
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.9-mad
patrick@ubuntu:~$

---

### Post by heimo on 2006-02-25
>  Nearly all the applications and packages mentioned on this page are found in the **universe** and **multiverse** repositories. See [AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto") for instructions on enabling the universe and multiverse repositories.

You can also try Automatix as suggested above.

---

### Post by madman0011 on 2006-02-25
im trying automatrix rite now ill tell u if it works

---

### Post by madman0011 on 2006-02-25
thnx it is working now thank you

---

### Post by sharke on 2006-02-25
Your Welcome
Regards
Sharke

---

### Post by engla on 2006-02-25
This is really on-topic here: Anyone know how handling of unrecognized formats is coming in dapper?

What we really need is for all the apps to say "this is an mp3 file, but you don't have the right codecs installed", and then point the user to a help page with docs, names of packages, and web links to that wiki page.

I know there is a spec on this, but what's the progress? It would help lots of users...

---

