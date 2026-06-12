---
title: "Lower resolution after updates to 8.10"
date: 2009-01-29
forum: General Help
---

### Post by onytz on 2009-01-29
Hello, 
After installing updates this morning, a system restart was required. After restarting, my screen resolution is lower, and I haven't been able to restore it.

Searching around in existing posts, I tried 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

which bumped the resolution further down, then I restarted, and from

```
System > Administration > Hardware Drivers
```

I selected 

```
NVIDIA accelerated graphics driver (version 177) [Recommended]
```

Restarting from there brought me back to the post-update resolution, which is still lower than the pre-update resolution I had before.

I'd like to get back to the pre-update resolution.

From ```
System > Preferences > Screen Resolution
```

The current selected, and highest available setting is

```
1024x768 (4:3)
```

But the pre-update resolution was higher (my monitor's native resolution is 1400x1050).

I've also read that editing xorg.config may help, but I'm not sure what edit to make to try it out. Here is my current version, if this is relevant:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```



Any suggestions? I'm considering re-installing Hardy from scratch, but I'd like to avoid that!

---

### Post by bixejo on 2009-01-29
Hi onytz,

My desktop computer is also equipped with a NVIDIA graphics card. When I tried to upgrade to Ubuntu 8.10 (I'm currently running 8.04) I got a warning pop-up window saying that there is no NVIDIA controller working properly in 8.10, and gave me the chance of canceling the upgrade, and of course that's what I did indeed.
 
I don't know more details, but I would suggest you to install Ubuntu 8.04 LTS instead of 8.10.

Good luck,

---

### Post by onytz on 2009-01-30
Thanks, bijexo. In fact, I did end up reinstalling 8.04 from scratch. Once I did, I had much less trouble with screen resolution. After getting it running right out of the box, the system couldn't detect my monitor's native resolution unless I played around a little in 

```
Applications > Other > Screens and Graphics
```

(which I had to add to the default menus by left-clicking on "Applications" and selecting "Edit Menus", then selecting "Screens and Graphics" from "Other".)

Incidentally, I don't remember seeing the same or a similar graphical interface in 8.10.

---

