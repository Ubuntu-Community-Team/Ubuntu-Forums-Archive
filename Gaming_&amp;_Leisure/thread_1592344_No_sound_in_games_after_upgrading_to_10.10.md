---
title: "No sound in games after upgrading to 10.10"
date: 2010-10-10
forum: Gaming &amp; Leisure
---

### Post by phoenix40uk on 2010-10-10
Just done the upgrade from kubuntu 10.04 to kubuntu 10.10. Now when trying to play a game (e.g. Unreal Tournament 2003 or 2004)not getting any sound. 
Getting the following message
open /dev/[sound/]dsp: No such file or directory

Can anyone offer any assistance or am I downgrading back to 10.04?

Thanks

---

### Post by Pimuzzo on 2010-10-10
i have got the same problem with ut99. i have tryed to create a simbolic link from /usr/lib to my System folder (of the game) with the command ln -s for the files:

libSDL-1.2.so.0.11.3 -> libSDL-1.1.so.0
libopenal.so.1.12.854 -> openal.so

but doesn't change, it still doesn't work.

---

### Post by Pimuzzo on 2010-10-11
i have read that there isn't the module of OSS in maverick kernel, so there are 2 solution:
1. recompile the kernel including OSS modules.
2. use padsp (at me causes a terrible delay in sound).

i'll wait other news.

---

### Post by phoenix40uk on 2010-10-12
yeah - I've been using padsp which does give sound, but as you have said, also has a delay

---

### Post by The Cog on 2010-10-12
At lease I have something with padsp, but it's bloody awful with that delay. Is recompiling the kernel really the only way?

---

### Post by rajeev1204 on 2010-10-13
Playing with the ingame audio settings along with no of speakers seems to trigger audio delay on and off for me in quake 4. So i cant really say if seting it to open al or dfault works, but toggling ( switching between either )  seems to work along with selecting surround speakers on / off.

Try it,.Else download the OSS 4 debs and install it , seems to solve problems for many people.

---

### Post by phoenix40uk on 2010-10-13
Didn't realise it was that simple. Installed OSS4 deb - games now have sound.

Headphone socket on laptop no longer working - but thats not a games issue so I'll post in another forum.

Cheers

---

### Post by The Cog on 2010-10-13
> **phoenix40uk said:**
> Didn't realise it was that simple. Installed OSS4 deb - games now have sound.
Sorry for being dumb but where did you get the oss4 deb from? I see in Synaptic that there is an oss4-base package, but the discription implies that it is for building kernel modules rather than being a completed oss driver.

---

### Post by phoenix40uk on 2010-10-13
[http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html)



Got it at the above URL. Can get the deb or the source code and compile it yourself.

---

### Post by z-vet on 2010-10-13
Installing OSS4 breaks my sound completely, even sound applet won't start. What did they do in this upgrade?

---

### Post by z-vet on 2010-10-14
Well, i've got it with padsp. Thanks guys. :)

---

### Post by alexandrius on 2010-10-15
padsp helped me :)

---

### Post by Zzl1xndd on 2010-10-15
padsp Also worked for me.

---

### Post by Rustybolts on 2010-10-15
Worked here with no noticeable lag in sound

---

### Post by alexandrius on 2010-10-16
Guys sound doesn't work for me in unreal tournament 2004, any ideas?

---

### Post by Rustybolts on 2010-10-16
Padsp worked for me on unreal tournament 2004.

---

### Post by rajeev1204 on 2010-10-16
What is padsp. Can you share your method please.

---

### Post by Rustybolts on 2010-10-16
```
cd /home/rustybolts/ut2004
padsp '/home/rustybolts/ut2004/ut2004'
```either type into terminal or create a .sh file and make it executable then you can use it as a shortcut.

---

### Post by alexandrius on 2010-10-16
yay, i my bad, padsp helps urneal tournament too!

---

