---
title: "Desktop and Windows went Totally black..!"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by milinda on 2007-07-17
HI.., I hav ubuntu festy with berly installed. I installed beryl, beryl-manger and emeral-thems. But when i run beryl-manager my desktop gone black. Also problem with windows. I can use 1 window ata time. Means i cant load two maximized windows at one time. When i do that ist window loading is ok. But when i load another fullscreen window it loding fully black...

I'm lil new to ubuntu.
and 
my video card is nVidia Corporation NV11 [GeForce2 MX/MX 400]..!

PLs.. I need some help here..!

---

### Post by Steveway on 2007-07-17
That is because your card runs out of memory.
Change the renderingpath to copy or use Aiglx.
It will be a little bit slower but it'll work.

---

### Post by hyperair on 2007-07-17
Strange, that usually doesn't happen to desktop windows. Anyway if you run Beryl on that card, make sure you turn off Blur completely. Disable the whole plugin. That greatly saves Video Memory and stops you from seeing these black windows so often. I've not used Beryl for extended periods of time with that card, because I only use a LiveCD on that system to ssh into this system if something hangs.

Anyway this system is running an nVidia GeForce 4 MX 440. Very similar to the GeForce 2 actually, and said to be the GeForce 2 on steroids. xD I'm not sure about the Video Memory on the GeForce 2, but this one has 64MB, and I can have quite a few maximized windows. Just make sure that blur is turned off. 

There's also a thread somewhere in [http://forums.opencompositing.org](http://forums.opencompositing.org) regarding the nvidia black window bug. You could run a search for that there and follow the instructions, or wait for me or someone else to search it up for you. I can't go looking for it now, it's 2 AM here and I need my sleep. Good night.

---

### Post by milinda on 2007-07-17
Thanx who replyed me ..! I forgot to mentioned that i installed xserver-xgl before install beryl. So how can a change the rendering to AIGLX. Can u pls guide me to how to do that. Once i rite click the buryl icon>Advnace beryl options> Rendering Platform>  to AIGLX. Then all got stuck. When i reboot OS not booting up. Then i reinstall ubuntu.

Another thing i'm using Wubi to install ubuntu...!

PLs help..!

Thanx u 2 for repling so quickly...!

---

### Post by elias@cpaefs.com on 2007-07-17
ubuntu 7.04 running on a Sony vaio vgn-s560p got the same problem with a nvidia 6200 go. This thread solve my problem with beryl

---

### Post by hyperair on 2007-07-18
You didn't post a link!

@milinda: Anyway you said you reinstalled Ubuntu? Just go to System->Preferences->Desktop Effects. Enable it. It'll go through some process of installing restricted drivers and whatnot. When it's done, restart your system. Go to Desktop Effects again, and disable it. Then install Beryl:
```

sudo apt-get install beryl beryl-manager emerald emerald-themes

```

Then run Beryl (Applications->System Tools->Beryl Manager)

---

