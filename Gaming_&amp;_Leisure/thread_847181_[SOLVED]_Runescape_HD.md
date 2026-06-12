---
title: "[SOLVED] Runescape HD"
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by okey666 on 2008-07-02
When I try to play the new Runescape high detail, the applet gets as far as "starting 3d library" and then gets stuck. My PC is well past the specs so it should work. I have tried various things but with no result, any one any idea?

---

### Post by Kinetic777 on 2008-07-02
Same problem for me; it hangs at "Starting 3d library" with no networking going on, no processing be done either.  >.<  I think it's just racism towards Linux

---

### Post by Exershio on 2008-07-02
People have been having a LOT of problems with the new RuneScape HD, not just Linux users. It seems it is very buggy software and that not many people can really get it to work. Your best bet is to wait for Jagex to fix it.

---

### Post by okey666 on 2008-07-02
Yeah, I think I'll do that. 

It sometimes hangs at "building interface" I have found. This happens when I have shut down the jvm and cleared the cache.

---

### Post by okey666 on 2008-07-02
Got so close! I got the loading screen but then it crashed.

---

### Post by dynamethod on 2008-07-02
it is in beta stages, so you have to expect things like that to happen

---

### Post by Phenax on 2008-07-03
Make sure you only have the Sun Java implementation, not OpenJDK or GCJ. Same goes for the browser plugin. Also, do this for full-screen support:

1. Open a linux terminal window.
   2. Type the following commands:
          * cd /usr/bin/X11
          * sudo cp Xorg Xorg-backup
          * sudo sed -i s/XINERAMA/ZINERAMA/g Xorg
   3. Then reboot your linux machine.


This worked for me and RuneScape works flawlessly. (besides the fact I can't actually login due to no members accounts)

---

### Post by lnxnut on 2008-07-03
I have 3 computers in the house all running Ubuntu 8.04 and Java 1.6 running, two are almost alike, both running radeon 9600 pro and the third one with a MSI motherboard with a built in nvidia chip for video (and yes cheap, its for a 7 year old).  I might also add the two running the radeon have 1 gig of ram each and the one running nvidia has 2 gig.  Both running the radeon I get the same place loading like you guys are, up to the 3d library stuff and it stalls. The nvidia loads perfectly and plays with no flaws at all.  I haven't fiddled with it much but I did the x11 stuff in the terminal but can't get full screen, but normally it really does look great, just can't place whether i need to just buy some nvidia cards or add another gig to these two computers.

---

### Post by okey666 on 2008-07-04
Got it! Can't log in because I am not a member, but it looks really good.

[COLOR="Red"]THE INSTRUCTIONS BELOW MAY MESS UP YOUR SYSTEM, KENETIC HAS USED THEM AD FOUND THAT THEY WORKED BUT YOU USE THEM AT YOUR OWN RISK[/COLOR]

Kinetic777 you may want to do what I did although I'm a bit of a newbie so this may be wrong:

The problem was that my GLX was out of date. I found out when I tried to use Java 3D. 
Fist get rid of xserver-xgl (according to:[http://ubuntuforums.org/showthread.php?t=834773]("http://ubuntuforums.org/showthread.php?t=834773") last post)
```
sudo apt-get remove xserver-xgl
``` 
and re-install the new nvidia drivers (note: this was for my G-Force card I don't know about others...). 
To do this search > glx in synaptic and look for the > nvidia-glx-new one and reinstall it.

It was then just a case of restarting. I hope that's all correct and it works!:D

---

### Post by Kinetic777 on 2008-07-16
Okey, that worked for me. RS works fine now  ^.^  hey, my RS name is the same as my screen-name

---

### Post by tubasoldier on 2008-07-16
Runs great in konqueror. My laptop (1.4 mhz) doesn't even meet "minimum" (1.5 mhz) specs as far as the processor goes. Loads more ram than needed though.

---

### Post by rasmus91 on 2010-05-03
okay, i can see this is old. But i can't even run it in SD, but only in Safemode, can any of you guys help?

---

### Post by ELD on 2010-05-03
If you need help try making a new topic not double posting in two very old ones.

---

### Post by philinux on 2010-05-03
> **ELD said:**
> If you need help try making a new topic not double posting in two very old ones.

Thread closed

necromonger

---

