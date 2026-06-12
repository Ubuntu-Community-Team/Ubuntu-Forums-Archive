---
title: "Searching for a good download manager"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Kelnoky on 2006-07-19
Hello guys,

I am in need of a good download manager that I can use with login sites like rapidshare.de for example. That means the manager needs to be able to handle several links that I take from a page and paste them to the queue. And of course the manager has to use a login and a password for sites like rapidshare. 
Currently I am using D4X which basically seems like a good manager but for some reasons every file I download from sites like rapidshare ends up as a 0kB plain text document. Even though D4X is downloading for the right amount of time (like 40 minutes for 100mb file with my slow 45kB/s connection). -.-

So, is it the fault of D4X or am I doing something wrong? In case it's D4X, what other download managers are out there and able to perform the needed tasks?

---

### Post by Kelnoky on 2006-07-20
*push*
Sorry for the double post, but this thread was on page 11 in no time...

---

### Post by mudra on 2006-07-20
downloader x may be right for you. I think it should be in the repositries.

Perhaps you could try apt-get install d4x

Mudra

---

### Post by Kelnoky on 2006-07-20
Err...well, the attempted help is appreciated but...I said that I am using D4X at the moment. Or rather I am trying to use it but it keeps on giving me empty files from rapidshare...

So no need to apt-get it.^^

---

### Post by Buffalo Soldier on 2006-07-20
I would recommend either Freeloader or Gwget (Download Manager). Both are available thru apt-get in the Universe repository.

> Freeloader is a nice GNOME download manager written in Python and supporting torrents.

> Gwget offers a GNOME front-end to the popular wget application, with
enhaced features, such as systray icon, multiple downloads and a
powerful preferences manager.

---

### Post by bluenova on 2006-07-20
I use Gwget, it does the job nicely and doesn't use much in the way of resources.

---

### Post by Kelnoky on 2006-07-20
Gwget does the job nicely? Err...can you download from login sites? Havent found that option yet. Same with freeloader.

Its really nice that you recommend me those programs, but without proper access possibility to login sites they are pretty useless for me. :)

---

### Post by mister_p_1998 on 2006-07-20
The Biggest failing Ive seen in Linux download managers, is that none of them make multiple connections to a single file as in Getright - up to 8 connections on one file, really speeds up slow connections.

---

### Post by havarka on 2006-07-20
wget

---

### Post by CyberCr33p on 2006-08-24
If you have premium account from rapidshare you can use wine and rapidget:

wine rapidget.exe

---

