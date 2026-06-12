---
title: "WoW Error"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by starfleetcaptainrob on 2007-03-24
Okay, I thought I was so close to be able to play WoW on my Ubuntu partition.  I guess that's why close only counts in horseshoes and hand grenades right?  Anyhow, I finally got the game installed with the expansion and all the updates downloaded and installed.  So finally I can login to a character so the game can create a Config.wtf file that I can edit according to the WoW tutorial.  So I log in and get this message:

[[IMG]http://img300.imageshack.us/img300/1387/wowerroral0.th.jpg[/IMG]](http://img300.imageshack.us/my.php?image=wowerroral0.jpg)

I'm hoping someone can help point me in the right direction.  I still need Windows for certain things, but the less switching back and forth I do the better.

---

### Post by hikaricore on 2007-03-24
Hmmm did you launch the game in opengl mode or d3d mode?

Which version of wine are you running, and what type of video card is in your system?

I won't be able to provide all the answers, but with more info myself and others
can help you the best we're able.

---

### Post by lakersforce on 2007-03-24
I was reading on the technical forums on [www.wow-europe.com](www.wow-europe.com) and lots of lots of users (primarily windows vista users) complain about this error #132. As of the date the Blizzard staff have not posted any satisfactory answers in blue.

EDIT: The flooding of the technical forums regarding "Error #132" began after the new patch EU-2.0.10. I myself have been experiencing rather frequent lockups, since the new patch.

---

### Post by starfleetcaptainrob on 2007-03-24
I'm running Wine 0.9.33 and I have an nvidia geforce 6800 xt 256 mb gddr3 agp card.

I did the registry edit detailed under Sammi's howto to change it to opengl, but I think I'm still running under d3d mode because I still have the double cursor error.  How would I be able to check this for sure?  (sorry, noob).

Also I've noticed that every time I try to log into WoW it makes me accept the new license agreement for the latest patch every time.  Very strange...

Any help would be appreciated and I can post any other info that may be needed...

---

### Post by lakersforce on 2007-03-24
You have to edit the Config.wtf file in the WTF folder of your WoW base install dir, and 
ad the following line to the top:

```
SET gxApi "OpenGL"
```

NOTE: If the WTF folder or Config.wtf file is not there, create them!

Make sure the user you intent to run the game with have read and write permissions to those files.

---

### Post by starfleetcaptainrob on 2007-03-24
Thanks all for your help!  The Config.wtf finally showed up and I was able to edit it.  WoW now runs nice and smooth!  I guess I was logged in long enough at one point for it to be created.  

:guitar:

---

### Post by hikaricore on 2007-03-24
> **starfleetcaptainrob said:**
> Thanks all for your help!  The Config.wtf finally showed up and I was able to edit it.  WoW now runs nice and smooth!  I guess I was logged in long enough at one point for it to be created.  

:guitar:

Glad you got it up and running :)  Happy adventures to ya.

---

