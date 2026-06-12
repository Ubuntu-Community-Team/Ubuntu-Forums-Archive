---
title: "Changing from ATI to Nvidia, any tips beforehand?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by CyberCod on 2006-09-05
Should I change the driver in xorg.conf from "ati" to "nvidia" before I reboot for the card-swap?

Does that even work like that? 
Does xorg even have built in Nvidia drivers?

Do I need to install the Nvidia drivers beforehand? 
Will it even show a screen if xorg.conf is not right?

I just want this to be as smooth as possible.  I've spent enough time troubleshooting lately, my brain is sore.

Just trying to cover my bases before I get knee deep in error messages (or worse no video output at all).

I thank you guys in advance.

I hope Ubuntu never dies down.  Ever.

Once I know what I'm doing, I'll be taking my turn in here.  I plan on bringing up my help-share ratio.

---

### Post by mlind on 2006-09-06
> **CyberCod said:**
> Should I change the driver in xorg.conf from "ati" to "nvidia" before I reboot for the card-swap?


You can do this if you wish. "nvidia" will make Xserver to use proprietary Nvidia driver. You should also install linux-restricted-modules and nvidia-glx package to get this working.
```

sudo aptitude install linux-restricted-modules-$(uname -r) nvidia-glx

```


> **CyberCod said:**
> 
Does that even work like that? 
Does xorg even have built in Nvidia drivers?


Yeah, that should be pretty much the changes you need to make. If xorg.conf has any ati specific stuff, remove those. Default Ubuntu install contains open source Nvidia driver "nv" which you can also use, but it doesn't handle 3D acceleration..

> **CyberCod said:**
> 
Do I need to install the Nvidia drivers beforehand? 
Will it even show a screen if xorg.conf is not right?


No. Xserver will just fail to load, but you can do necessary stuff from command line too. Kernel (?) falls back to simple command line interface if  there's something wrong with Xserver configuration.

---

### Post by CyberCod on 2006-09-06
thanx for the info, I'll start out with "nv" and then get the proprietary driver working afterward.

Seems the most expedient way to do it.

---

### Post by mlind on 2006-09-06
> **CyberCod said:**
> thanx for the info, I'll start out with "nv" and then get the proprietary driver working afterward.

Seems the most expedient way to do it.

Yeah, using "nv" for starters sounds safe. It's probably best to backup your current xorg.conf too, and "reconfigure" xserver (generate xorg.conf for your harware) once you've got nvidia gfx card in slot.
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by CyberCod on 2006-12-12
--UPDATE--
Went off without a hitch... later got the proprietary drivers working and have full 3d accelleration, GLX, World of Warcraft, etc.

Thanx for the tips.

---

