---
title: "Apt-Get Upgrade withholding packages"
date: 2005-04-21
forum: Desktop Environments
---

### Post by cajunaggie on 2005-04-21
I ran the apt-get upgrade command two weeks ago and it gave me this message
```
The following packages have been kept back:
 mplayer-386
``` 
I figured it was just a problem with MPlayer because I've been having issues with MPlayer since Day 1 of my introduction to Linux.

However two days ago I ran the apt-get upgrade command and recieved this message:
```
The following packages have been kept back:
  libavcodeccvs libpostproc0 mplayer-386
``` 

Any idea what's going on? :-?

---

### Post by TravisNewman on 2005-04-21
Yeah, I've got quite a few. I think it's an issue with mixing repositories and some dependencies not matching up. I have the three you have and a couple more.

---

### Post by dewey on 2005-04-21
To install mplayer you had to mess with the repos a bit to get the proper versions of some of the files.

Does a
$sudo apt-get dist-upgrade
Solve the problem?  If not, don't worry about it.

---

