---
title: "CounterStrike 1.6 ATI Radeon X1300 pro (512MB) issue"
date: 2007-05-31
forum: Gaming &amp; Leisure
---

### Post by rabidbager on 2007-05-31
I am a for Windows wiz and Linux Newbie and I am struggling to get my CounterStrike 1.6 working well. I was able to install the latest drivers for an x86 64bit architecture. However when I try to run CS through steam is loads but slowly. And running the game is extremely choppy. My driver details under steam recognize my software support for DirectX 9.0 but my hardware support only for DirectX 6.0. (CS requires a minimum of 7.0). I know my video card does not need an upgrade because previously I ran CS through steam on Vista before I installed Ubuntu Feisty Fawn. Any thoughts?

---

### Post by blazercist on 2007-05-31
whats the output of

fglrx

wine --version

and which sound driver are you using in winecfg?

---

### Post by rabidbager on 2007-05-31
matt@matt-desktop:~$ fglrx
bash: fglrx: command not found

matt@matt-desktop:~$ wine --version
wine-0.9.37

i dont know the other info where would i get that

---

### Post by adam0509 on 2007-05-31
not fglrx, but :

$ lsmod | grep fglrx



Should give result, try it !!


If it don't work, try "desktop mode" in wine (800*600 for example) and tell us if it works better

---

### Post by rabidbager on 2007-06-02
lsmod | grep fglrx gave no result. I have a feeling that could be a problem....how do I fix that.

---

### Post by Alex Fernandez on 2007-06-02
Firstly, make sure that the fglrx driver is installed correctly:

[http://ubuntuforums.org/showthread.php?t=221320&page=21](http://ubuntuforums.org/showthread.php?t=221320&page=21)
and
[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

Or any one of the other guides

Secondly, once you do have that driver installed, try running the game in OpenGL mode.

---

### Post by lordhebe on 2007-06-02
Also make sure your sound is set to OSS, and not ALSA. ALSA runs really slowly for me.

---

### Post by rabidbager on 2007-06-05
K now it opens but then the screen goes black and mouse blinks rapidly after the loading screen.....Son of a biscuit

---

### Post by adam0509 on 2007-06-08
diable shader.


The game should be launched with OpenGL, so I guess you have to add -opengl before launching game (propreties etc..)

---

