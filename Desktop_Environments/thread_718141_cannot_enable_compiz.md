---
title: "cannot enable compiz"
date: 2008-03-07
forum: Desktop Environments
---

### Post by Anonimoes on 2008-03-07
Today I've been trying to enable compiz on my ubuntu 7.10 box. I've tried the " restricted drivers manager ", manual install of ati's drivers using the howto page and installing the ati drivers with envy. all to no avail. I still can't enable compiz...

fglrxinfo currently says:
```
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

I know this means the mesa driver is used, the strange thing is that I just installed the ati drivers using envy and rebooted, then I get this.... When I used the restricted drivers manager fglrxinfo did say the ati driver was used but glxinfo | grep direct showed a "No".

I'd very much like to enable compiz but am at a loss as to what to do now.

---

### Post by uberlube on 2008-03-07
using an ATI card with compiz is a real hit or miss situation. You need nvidia my friend.

---

### Post by boeing777 on 2008-03-07
enable Restricted Drivers, then enable Compiz,

what does it say?error Message???

---

### Post by Anonimoes on 2008-03-08
When I try to enable desktop effects after I've installed the restricted driver a little errorbox tells me that "desktop effects could not be enabled" When i try to start compiz manually through the commandline it says that direct rendering is off and that it couldn't find a whitelisted driver... (I have an Ati Radeon 1950pro).

So I guess it's just not possible for me to use compiz while using the closed source driver? As I see it this is merely a driver issue and there are lots of people who are able to use compiz with the latest drivers by Ati...

---

### Post by Anonimoes on 2008-03-10
> **uberlube said:**
> using an ATI card with compiz is a real hit or miss situation. You need nvidia my friend.

Well, I guess sadly you are right. This weekend I succesfully enabled compiz on an older ati card (9600 pro). Somehow it worked on this card with the restricted driver and not on my 1950 pro... I knew Nvidia is the way to go if you want to be sure about using compiz but didn't take that into account when buying my 1950 pro.

I guess no one has a clue as to how I might get compiz to work with my 1950 pro in another way?

---

### Post by Victormd on 2008-03-10
I have the EXACT same issue with an ATI X300...
thank God I'm upgrading to a GeForce 8800 GT!!!

---

### Post by Victormd on 2008-03-10
Check out this How To... it worked for me...
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

### Post by santiagoward2000 on 2008-03-11
> **uberlube said:**
> using an ATI card with compiz is a real hit or miss situation. You need nvidia my friend.

Hi!
Well, actually it's not that hard (at least in my case). The problem is that you need to install XGL. In Gusty is quite easy, just install **xserver-xgl** from the repositories and restart your computer. Then try to run Compiz.
It worked great with my ATI, perhaps I'm just lucky :)
Cheers!

---

### Post by Anonimoes on 2008-03-11
Okay, now what: I've followed the tutorial and now when I try to scroll through webpages it's slow as hell... My fglrxinfo however states the ati driver being used. glxinfo | grep direct says direct rendering is not on though. When I try to enable compiz via the appearance menu it can't be enabled. When I try it via the commandline with sudo compiz --replace it says:

```

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

```

This suggests compiz isn't correctly installed so I reinstalled all compiz related packages, to no avail though... I'm really getting tired of this 1950 pro card by now and guess it will just not work for me on this system...

---

### Post by Victormd on 2008-03-11
Sorry to hear that! This is the first time I have a system with an ATI so I can't help much... I'll check back if I find anything new...

---

