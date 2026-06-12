---
title: "Not playing .wmv files"
date: 2006-07-19
forum: Desktop Environments
---

### Post by abhiomkar on 2006-07-19
I have xine, mplayer, VLC ...
but i am not able to play wmv video. When i play the video only audio is comming instead of video.

how can i play wmv format files ?

---

### Post by Jagot on 2006-07-19
w32codecs:

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by palsyboy on 2006-07-19
Another way to do it will be to add the following lines to /etc/apt/sources.list:
```
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free
```
After that, run:
```
sudo apt-get update
sudo apt-get install w32codecs
```
Either way will work.

---

### Post by FredB on 2006-07-19
Tell me if I am wrong, but freecontrib.org was down a few days ago...

---

### Post by palsyboy on 2006-07-19
Just ran sudo apt-get update, and it hit the server just fine.  It should be up.

---

