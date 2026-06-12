---
title: "need help to install games"
date: 2006-11-01
forum: Gaming &amp; Leisure
---

### Post by DougieFresh4U on 2006-11-01
I have downloaded 3 games from 'The Linux Game Tome'. they are tar files and I cannot EVER seem to get a tar file installed. can some one please help? if you need to know more about what games or what ever, let me know. they are simple games that do not require alot of tricks or extra hardware. thank you

---

### Post by meng on 2006-11-01
Yes it would help a lot if you specified which games, where you downloaded from and **most importantly** what you tried already.

---

### Post by DougieFresh4U on 2006-11-01
Hi meng! I downloaded 3 Mahjong games From the Linux Game Tome. These are the 3 files: majongg3d-0.96.tar.bz2    mj-1.7-linux-i386.tar.gz   &   mahjong_lin.tgz      and they in my /home/dougie.  I do not know where to go from here

---

### Post by Perfect Storm on 2006-11-01
Extract the file tarball, look for a readme.txt and/or read from their homepage how it needs to compile and what libs + -dev and headers are needed.

---

### Post by meng on 2006-11-01
> **DougieFresh4U said:**
> Hi meng! I downloaded 3 Mahjong games From the Linux Game Tome. These are the 3 files: majongg3d-0.96.tar.bz2    mj-1.7-linux-i386.tar.gz   &   mahjong_lin.tgz      and they in my /home/dougie.  I do not know where to go from here
So if I understand you correctly, you haven't actually done or tried anything other than downloading the tar files. If this is the case, you need to untar the files, and then compile from source. Look here
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

although note for the .tar.bz2 file you need to use syntax
tar jxvf (not tar zxvf)
in order to uncompress the file.

What AI says about dependencies is also important, so read the README file (or similar) within the un-tared files/directory.

---

