---
title: "i810 incredibly slow on edgy"
date: 2007-02-12
forum: Desktop Environments
---

### Post by gp2x on 2007-02-12
Hi all

Just installed Edgy on a brand new dual core PC.

After booting, everything is *incredibly* slow. I mean, sssllloooowww - it takes 10 seconds to draw the login screen. The desktop is extremely slow, taking 20 seconds or more to start a terminal. I mean, the performance is BAAAAD. Its so bad, it appeared in a Michael Jackson video. Its so slow I could render the gnome desktop faster with a piece of paper and a pack of Faber Castels.

I thought it might be the i810 drivers, but I tried VESA with zero improvement.

The desktop is practically unusable in this state. Where can I begin to look?

Thanks

ps. I forgot to mention, I went into the BIOS to ensure no other devices were on the same IRQ as the VGA card (years ago this would sometimes cause problems) and Ive found that linux cant even see the interrupt? I know the VGA is on IRQ 5, lspci -v shows that it is on 5, but /proc/interrupts shows nothing is on 5.

pps. Oh, also, we had to use pci=nommconf to get this thing to boot

---

### Post by jpeddicord on 2007-02-12
> **gp2x said:**
> Its so slow I could render the gnome desktop faster with a piece of paper and a pack of Faber Castels.Nice analogy. :)

One reason it is going slow might be because Direct Rendering is not enabled. To check for this, boot up the system in recovery mode (from the GRUB menu) and type the following:```
glxinfo | grep rendering
```It should give you a yes or no answer. If it isYes, then it is a problem with something else. If it gives a No, then we need to get that fixed. :)

---

### Post by gp2x on 2007-02-12
Thanks, but Ive solved it.

I found that other people here have identical desktop PCs and are running Edgy just fine (our entire development dept are installing Ubuntu in preference to Windows, much to the chagrin of the technical services dept..... they seem to have caught on though because I got my PC sans OS).

I reinstalled and everything works fine. I mean, dont get me wrong, the chipset is an absolute pile of pigsnot, but at least it runs decently now. If I try to run glxgears I get 'libGL warning: 3D driver claims not to support visual 0x5a' which is something Ill have to figure out, but 2D performance is acceptable.

What did I do differently? The only difference is that I had the network plugged in the second time. Seriously, that was the only difference. Weird.

Thanks for your interest though!

---

### Post by jpeddicord on 2007-02-12
It probably just was a random occurrence where the hardware was not detected correctly. Good thing it works now though!

:)

---

### Post by gp2x on 2007-02-12
indeed, however I wont be recommending the Intel 965Q chipset to anyone anytime soon :)

---

### Post by jpeddicord on 2007-02-12
The Intel Integrated graphic solutions are actually fine for most people, including me. You get 96MB of memory, and beryl/compiz buns without any slowdowns. Plus as an added bonus, you get open-source drivers. :)

---

### Post by gp2x on 2007-02-13
I cant get 3D to even run (see above) even tho DRI is enabled etc.

2D performance is piss. I drag a terminal around the screen and watch the pretty trails - weeeeee!!!!

96M you say? Perhaps Ill increase my 'VideoRam' setting and see what happens. Perhaps it will improve.

Could you possibly send me your xorg.conf? 

Thanks

---

### Post by jpeddicord on 2007-02-13
I'm only going to include the part about my display, because I've hacked the rest of it up for tablet support. Don't directly paste this, it will not work. Make sure you keep your old monitor settings instead of mine, and remember to backup the file in case something goes wrong.```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ramjet_1953 on 2007-02-13
Download [COLOR="Red"]915resolution[/COLOR] from the repositories, using Synaptic.

Read the notes that come with it and I think that you will be surprised how well the Intel chipset works under Linux.

Regards,
Roger 8-)

---

### Post by gp2x on 2007-02-14
By disabling ipv6 I seem to have gotten some decent 2D performance finally

However, 3D still doesnt work - DRI is enabled etc, but running glxgears gives me:

libGL warning: 3D driver claims to not support visual 0x5a
DRM_I830_CMDBUFFER: -22


Supposedly this is a known issue and a fix is upstream. Just wondering why you guys dont suffer from it?!?


EDIT: I cant use 915resolution, because I have a 965Q chipset :( Looks to be what I need though!
EDIT: After hacking a bit I managed to use 915resolution..... not sure what it does though :) I still need a fixed version of libgl-mesa-glx

---

### Post by gp2x on 2007-02-15
Now Ive managed to cobble together working DRI support, but Beryl/XGL just produces a white screen. 

Bah!

---

### Post by akudewan on 2007-02-15
> **gp2x said:**
> Thanks, but Ive solved it.

I found that other people here have identical desktop PCs and are running Edgy just fine (our entire development dept are installing Ubuntu in preference to Windows, much to the chagrin of the technical services dept..... they seem to have caught on though because I got my PC sans OS).

I reinstalled and everything works fine. I mean, dont get me wrong, the chipset is an absolute pile of pigsnot, but at least it runs decently now. If I try to run glxgears I get 'libGL warning: 3D driver claims not to support visual 0x5a' which is something Ill have to figure out, but 2D performance is acceptable.

What did I do differently? The only difference is that I had the network plugged in the second time. Seriously, that was the only difference. Weird.

Thanks for your interest though!

Maybe it was the "hostname". I remember when I had setup the wrong hostname, my PC was acting just like yours

---

