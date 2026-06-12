---
title: "How to install The Ur-Quan Masters?"
date: 2006-05-03
forum: Gaming &amp; Leisure
---

### Post by glotz on 2006-05-03
Hi there! How do I install [The Ur-Quan Masters](http://sc2.sourceforge.net/)? There seems to be a version 0.3 in synaptic package manager (uqm) but I'd like to test the 0.5 version announced on the home site. No help available in the [Wiki](https://wiki.ubuntu.com/Games). Linux newbie here. Not a clue. :cool: 

I remember playing the original label [Star Control II - The Ur-Quan Masters](http://en.wikipedia.org/wiki/Star_Control_II#Star_Control_II) when my father bought it to me at christmas some ten years ago. It was great! I'd love to relive it...

Thanks for your help.

---

### Post by shapht on 2006-05-03
I added one of these debian repos to synaptic (check the README if you need help on writing the apt line entry):

[http://uqm.debian.net/](http://uqm.debian.net/)

I remember using testing, since unstable needed newer libs than breezy, but try it out i guess.

---

### Post by glotz on 2006-05-03
Got the apt line but when trying to mark uqm for install it sez [quote=synaptic]uqm:
  Depends: libogg0 (>=1.1.3) but 1.1.2-1 is to be installed
  Depends: libvorbis0a (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
  Depends: libvorbisfile3 (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
 Depends: uqm-content but it is not going to be installed

[/quote]

---

### Post by shapht on 2006-05-03
Ahh, they moved newer versions into Testing. Ok that means you have to either compile the source by hand, or keep digging till you find some debs somewhere...  

Sorry my help was out of date!

---

### Post by glotz on 2006-05-03
You're welcome. I think I managed to find and install those libs by
[http://packages.debian.org/testing/libs/libogg0](http://packages.debian.org/testing/libs/libogg0) > i386 > sudo dpkg -i [package name]
[http://packages.debian.org/testing/libs/libvorbis0a](http://packages.debian.org/testing/libs/libvorbis0a) > i386 > sudo dpkg -i [package name]
[http://packages.debian.org/testing/libs/libvorbisfile3](http://packages.debian.org/testing/libs/libvorbisfile3) > i386 > sudo dpkg -i [package name]

Now downloading uqm! :)

---

### Post by MrHulk45 on 2006-05-03
I ran across your thread and was reminded about the game from long ago. I followed the your info and was able to download all the required packages and get the game running. 

 Thank you  MrHulk

---

### Post by glotz on 2006-05-03
Great to hear that. Was just coming back myself to report that I got it working too. Great fun! Incredible retro gaming! :)

EDIT: Now here's my Wiki entry [https://wiki.ubuntu.com/TheUr-QuanMasters](https://wiki.ubuntu.com/TheUr-QuanMasters)

---

### Post by Indras on 2006-06-29
I feel obliged to update this.  In Ubuntu Dapper Drake 6.06, to install Ur-Quan Masters 0.50, simply add the following line to the end of your /etc/apt/sources.list:

```
deb http://uqm.debian.net/ testing/
```

Then run 'sudo apt-get update' and go into Synaptic Package Manager.  Install uqm, uqm-content, uqm-voice, and uqm-music.  It will balk at you about authentication, and the fact that they are testing packages, but it works.

---

### Post by Frem on 2006-07-12
Don't need any Debian servers. I think I got it off the Ubuntu Multiverse.

---

### Post by glotz on 2006-07-12
Evolution before our very eyes! :) (The newest version won't neccessasily be the one found in the repositieries.)

---

