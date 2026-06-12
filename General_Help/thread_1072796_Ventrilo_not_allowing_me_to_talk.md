---
title: "Ventrilo not allowing me to talk"
date: 2009-02-17
forum: General Help
---

### Post by Beautysdeath on 2009-02-17
Ok I am having a serious issue with ventrilo, I can not talk to people on it even if it is in focus. I am on a Compaq Pressario SR1820NX using on board sound. I have search over a dozen forums and posts and tried all the suggestions to get this to work I hear everyone just fine. No matter what I do I can not be heard. The system is 64bit I am running Xbuntu 8.10 x64. I have a sound blaster audigy se card I can put in but it does nothing more that my on board sound as far as this problem so I removed it any one that has gotten this working please help me.

---

### Post by biovore on 2009-02-17
ventrillo I am guessing your running it under wine.  You need to setup the wine sound system to use alsa.  Also mic settings on audigy 2 are strange at best.  I there is some weird setting you have to change else you get nothing.  I also wouldn't trust the gui sound mixers.. they tend to lie.   open up a shell and type alsamixer and go trough and set all the levels.  If you have 2 sounds cards in the machine you may also be recording from the wrong card. aplay -l will list the sounds cards on your system.

I did get ventrillo 3 to work.. but its a pain. and you need to steal the msgsm.acm file off a windows XP machine to get it to work.

---

