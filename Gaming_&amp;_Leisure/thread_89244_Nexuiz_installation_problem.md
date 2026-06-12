---
title: "Nexuiz installation problem"
date: 2005-11-12
forum: Gaming &amp; Leisure
---

### Post by klemens on 2005-11-12
Trying to install nexuiz,

root@Home:~# sh nexuiz_1.2.1-english.run
Verifying archive integrity... All good.
Uncompressing Nexuiz 1.2.1-english Installer.................................................................
gzip: stdin: invalid compressed data--crc error


Gdk-WARNING **: locale not supported by C library
loki_setup: Read failure on data.tar.bz2
root@Home:~#

I'm getting this error what should i do?

---

### Post by slux on 2005-11-12
Sounds like your download is corrupt although the part about verifying the archive integrity speaks against that. I'd check the md5sum / download again.

---

### Post by lateo on 2005-11-12
1. download it once more, installer may be corrupted.

2. root is not necessary. :rolleyes: 
to keep full simple-user rights on the game files u should create a 'games' directory in your /home and install every single game.run or game.sh in it.
this is specialy usefull for games that need to download files (ET, etc.). or prepare yourself to be root most of the time ; which is not good.

---

### Post by slux on 2005-11-12
Installing as root might be a good idea if you've got a multi-user system, /usr/local is a fine place to put things. Games like ET should know to download stuff into the user's own directory if installed system-wide.

---

### Post by lateo on 2005-11-12
[QUOTE=slux]Installing as root might be a good idea if you've got a multi-user system, /usr/local is a fine place to put things. Games like ET should know to download stuff into the user's own directory if installed system-wide.[/QUOTE]

of course this is right. but how many of us do REALLY need/use multi-user config? then, how many of these do need to share a game?
not so much :rolleyes:
your mother or girlfriend does not play the same games u enjoy ;)

---

