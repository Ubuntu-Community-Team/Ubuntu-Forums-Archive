---
title: "Xgl screwing up"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by drchaos619 on 2007-10-03
I used envy to install drivers for my ATI 9800 pro so I could watch videos without a low fps. I had compiz, gnome and emerald installed and everything worked just fine with the exception of the video

I install the new drivers and BAM, everything gets thrown out of wack. Gnome with XGL sessions show a glitched up screen. I heard XGL was for the fglrx drivers and when I enter fglrxinfo i get

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I'm a linux noob and tried to fix this the best I could. I completely uninstalled compiz, gnome, ati drivers and emerald. I reinstalled them in the non gui mode and still, glitched up xgl session.

I tried envy again and all of a sudden, compiz started working! I hit emerald --replace and I'm back to square one. 

pleassssse help

---

### Post by drchaos619 on 2007-10-04
annnnnny help would be much appreciated

---

### Post by HokeyFry on 2007-10-04
i had the exact same issue

hang on ill post the thread i followed in a sec, just want you to know someone's helping u

---

### Post by drchaos619 on 2007-10-04
thanks. I posted this about a week ago and no one replied. I've been trying to figure it out myself. I'm sure you know how that worked out.

---

### Post by HokeyFry on 2007-10-04
alright, i now see u used envy to install ur drivers so i dunno

try this
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9)

i know you already have your drivers installed but following the feisty instructions fixed this issue for me (though I had to continue on to the Edgy section). I also am unsure if anything detrimental would happen if you followed this guide since your drivers are installed. I can't see anything bad happening but maybe someone else will read this thread and correct me if I am wrong.

sorry, but this is as far as my eye candy experience goes. Hope this helps though!:)

---

### Post by drchaos619 on 2007-10-04
hey its certainly worth a shot. There are some things in there I've been looking for but just couldn't find. You saved me alot of trouble. thanks

---

### Post by HokeyFry on 2007-10-04
if worse comes to worse and its important enough to you to have eye candy, the method i posted will most likely work on a fresh install

but, like in my case, i cant just up and redo my system any old time, i use this for school so i have to be careful *COUGH*MEDIADIRECT BUTTON*COUGH*




im sure anyone with a dell media direct button knows the pain and suffering it can cause...

---

### Post by drchaos619 on 2007-10-04
well, i managed to get rid of the MESA config

HOWEVER!

now gnome with xgl session are still glitchy and run slow. what I mean is that the graphics aren't rendered properly or anything

I don't know if its a driver configuration problem or Xorg.conf problem 

any ideas?

---

### Post by drchaos619 on 2007-10-04
heres a nice screenie of what im getting when i log into gnome with xgl

---

### Post by Jouke74 on 2007-10-04
XGL SHOULD show the mesa drivers as it uses the Mesa libraries for rendering your screens! In the background the X-server, which is backing up your XGL server, the FGLRX drivers are indeed doing their work as they should. 

In principle (layer1) X-server + FGLRXdriver and on top (Layer 2)  XGL server + Mesa rendering gives compiz efects. Only layer 2 is shown on your screen when you use XGL.

The new FGLRX drivers and older XGL don't seem to cooperate very well together. There are already many threads about this on the forum. Most stable system, but definitively not the fastest can be obtained using the Ubuntu FGLRX drivers and XGL server. If required a second X-server session can be started to watch video or play games (but this requires some tinkering with system and config settings).

---

### Post by drchaos619 on 2007-10-04
> **Jouke74 said:**
> XGL SHOULD show the mesa drivers as it uses the Mesa libraries for rendering your screens! In the background the X-server, which is backing up your XGL server, the FGLRX drivers are indeed doing their work as they should. 

In principle (layer1) X-server + FGLRXdriver and on top (Layer 2)  XGL server + Mesa rendering gives compiz efects. Only layer 2 is shown on your screen when you use XGL.

The new FGLRX drivers and older XGL don't seem to cooperate very well together. There are already many threads about this on the forum. Most stable system, but definitively not the fastest can be obtained using the Ubuntu FGLRX drivers and XGL server. If required a second X-server session can be started to watch video or play games (but this requires some tinkering with system and config settings).

Ah I see, hence why the driver update screwed me over. Is there a way to remedy this? My old fglrx worked beautifully. I just couldn't deal with my videos low fps. is there a way to revert this?

---

