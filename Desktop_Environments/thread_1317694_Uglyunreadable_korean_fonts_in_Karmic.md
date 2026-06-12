---
title: "Ugly/unreadable korean fonts in Karmic"
date: 2009-11-06
forum: Desktop Environments
---

### Post by bakaeigo on 2009-11-06
Hey all,

I'm running a fresh install of 9.10, and pretty much every application displays Korean text in an ugly and often unreadable font (see attached image.) I have a wide range of Korean fonts installed, and Openoffice displays Korean well, according to the font I choose. 

How can I fix the display problem for the rest of my applications?

---

### Post by bakaeigo on 2009-11-07
bump

---

### Post by carlos08 on 2009-11-07
I suggest you **uninstall ttf-wqy-zenhei** from your system.  It worked for me on 
a fresh install of Ubuntu 9.10 64-bit.  Amazing how a single new default font can 
cause such a regression.  I guess the developers should have tested the font 
more thoroughly before setting it to override the Un fonts as the default for Hangul.  
I've seen this issue in recent Debian and PcLinuxOS releases, as well.  

If you need more specific instructions, just do the following:  
**Open Synaptic** via System > Administration > Synaptic Package Manager
[Enter your password for administrative privileges]
**Search** for **ttf-wqy-*** in the search box
You will see that **ttf-wqy-zenhei** is installed
Click on the green check box next to the package, 
and select **Mark for Complete Removal**
**Click Apply**

That should solve the problem.  
If you really need Chinese or Japanese fonts, I think there are workarounds 
that don't require uninstalling the font package(s), but I haven't tried them myself.  

For reference:  
[https://bugs.launchpad.net/ubuntu/+source/ttf-wqy-zenhei/+bug/475240](https://bugs.launchpad.net/ubuntu/+source/ttf-wqy-zenhei/+bug/475240)
[http://www.ubuntu.or.kr/viewtopic.php?f=10&t=8232](http://www.ubuntu.or.kr/viewtopic.php?f=10&t=8232) (in Korean)

Good luck!

---

### Post by bakaeigo on 2009-11-07
Carlos08, thank you so much. Your instructions worked :D

---

### Post by sulgorae on 2009-11-12
thanks so much guys. that works perfectly

---

### Post by ubun_two on 2009-12-07
This also fixed the ugly Japanese font that I was seeing on my system.

---

### Post by jrrader on 2009-12-16
This fixed it for my wife's computer too.  I hope this font is removed in the future.

---

### Post by G2k on 2010-01-25
Fixed!

Wow they should really get rid of that horrible font..

---

### Post by AncientPC on 2010-02-23
> **carlos08 said:**
> I suggest you **uninstall ttf-wqy-zenhei** from your system.  It worked for me on 
a fresh install of Ubuntu 9.10 64-bit.  Amazing how a single new default font can 
cause such a regression.  I guess the developers should have tested the font 
more thoroughly before setting it to override the Un fonts as the default for Hangul.  
I've seen this issue in recent Debian and PcLinuxOS releases, as well.  

If you need more specific instructions, just do the following:  
**Open Synaptic** via System > Administration > Synaptic Package Manager
[Enter your password for administrative privileges]
**Search** for **ttf-wqy-*** in the search box
You will see that **ttf-wqy-zenhei** is installed
Click on the green check box next to the package, 
and select **Mark for Complete Removal**
**Click Apply**

That should solve the problem.  
If you really need Chinese or Japanese fonts, I think there are workarounds 
that don't require uninstalling the font package(s), but I haven't tried them myself.  

For reference:  
[https://bugs.launchpad.net/ubuntu/+source/ttf-wqy-zenhei/+bug/475240](https://bugs.launchpad.net/ubuntu/+source/ttf-wqy-zenhei/+bug/475240)
[http://www.ubuntu.or.kr/viewtopic.php?f=10&t=8232](http://www.ubuntu.or.kr/viewtopic.php?f=10&t=8232) (in Korean)

Good luck!
This fixed my issue as well.  I agree with everyone else that this font needs to be removed.

---

### Post by Decimatio on 2010-03-03
Thank you very much.

&#44048;&#49324;&#54633;&#45768;&#45796; :)

---

### Post by tora201 on 2010-03-19
Yeah! Works here too. Japanese fonts all looking *much* better!

---

