---
title: "Major 2D Tearing"
date: 2005-06-27
forum: Gaming &amp; Leisure
---

### Post by BoyOfDestiny on 2005-06-27
Hi everyone, I have Ubuntu 5.04 working great on my dell inspiron 6000 (hurray for $750 off deal!).

But... tearing occurs in zsnes, xmame, advmame, nintencer, etc... 
This happens when there is fast movement horizontally, and is noted as a problem in xorg according to freedesktop.org... 
[http://xorg.freedesktop.org/wiki/XorgPerformance](http://xorg.freedesktop.org/wiki/XorgPerformance)

I have dbe enabled (by ubuntu)... and I could not use the fglrx with the laptops radeon X300 (M22). 

This occurs under windows as well, but there are "vsync" or "triple buffering" or some other options that prevent it. Is there some way to enable vsync (I've tried for example to pass the commandline option in zsnes, it was gone from the gui in the linux version, nothing happened). Please note, even it means performance loss I would really like to resolve/reduce this.

Last bit of info

1280x800 15.4 LCD (dunno any other specs about the monitor), perhaps changing some of the "refresh values" for vertical would help? I tried DisplayPriority...to no avail)

Thanks in advance!

---

### Post by Omnios on 2005-06-27
You might want to try a color depth of 16, doing that seemed to fit up my nvidia gforce2 100/200 64 meg glxgears whent from 400 to 780 fps. More importantly I had less app tearing (still happenes but only at higher movement speeds.)

---

### Post by BoyOfDestiny on 2005-06-27
Thanks, I tried it, but same problem...  ](*,) 
I even lowered it to 8 to make sure my changes were working... 
The same tearing and banding...doesn't seem to occur in regular app use, just games. 
It will occur in games like mega man x2 or super mario 3. Anywhere there is fast horizontal scrolling. 
It has something to do with the vertical refresh...

---

### Post by Omnios on 2005-06-27
One thing you can check is  the make and model off the back of the monitor, get the specs off line, I got mine off off a windows ini driver file. Check the specs against whet it is in the xorg.conf. I found mine to be way off. Probably wont help but I found the autodetects where way off for mine.

---

### Post by Omnios on 2005-07-01
Im not shure how your graphics card set up is I use nvidia. I came accross some threads about slow computer performance which pointed out some agp video settings etc and how to blackport certain agp setting. After doing this I noticed a big inprovement in non 3d performace the graphics looked clearer and there was less tear problems.

---

### Post by BoyOfDestiny on 2005-07-03
First I want to say thanks, but still having trouble. 

What I've done is change "ati" to "radeon" and put some of the options...fglrx I notice (when I ran its x config, it has an option for enabling vertical sync.) However, no matter what I try, X does not load when I use fglrx, I notice during failsafe boot that it loads the ATI modules etc... Anyway I fixed it with nano and this is what I have now...

	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
        Option		"UseFBDev"		"false"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"true"
        #Driver          "fglrx"
        #Option "VideoOverlay" "on"
        #Option "OpenGLOverlay" "off"
        #Option "UseInternalAGPGART" "no"

With things as they are, this is what I get when I type fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Anyway it seems fglrx would solve my problem (if I could get it to work... Dell inspiron 6000 with A06 bios (just flashed it with bootable cd). I really hope there is or will be an option to enable vertical sync in the open source driver...(my desktop has a radeon 9200).

Again, thanks in advance

---

### Post by Omnios on 2005-07-03
Not shure about your graphics card but I whent to the nvidia web site and read the read me for nvidia, I found this full of usefull xserver config options which realy helped me. I also found that it was loading stuff it shouldnt such as item-agp etc which I blacklisted so it didnt load. Xorg is fairly new with a few bugs which hopefully they will fix as time goes on. I used these term commandds to find what the actual set up was.

tom@Main:~$ lsmod |grep -i agp
                       this told me I was using inte-agp

tom@Main:~$ cat /proc/driver/nvidia/cards/0
                        Video card info and type

 Basicly it will tell you whats driving 2d graphics.

---

### Post by BoyOfDestiny on 2005-07-06
I found a post from 2003 that seems to be the problem for me:
[http://www.mail-archive.com/xmame@toybox.twisted.org.uk/msg06162.html](http://www.mail-archive.com/xmame@toybox.twisted.org.uk/msg06162.html)

> To eliminate tearing, xmame needs to sync with the vertical retrace.
> Unfortunately, XFree86 doesn't have a sane, consistent way to do this. 
> Some drivers can do it, most don't.

"I use DirectFB as (xmame.)SDL backend which does proper vsync if you
use a radeon or Matrox card. I've created custom video modes
in /etc/fb.modes to drive the arcade montior with exactly the same
vertical refresh rate the games need."

So my question is... have things changed at all, and any advice about using directFB on an lcd screen on/instead of X? (forgive the n00bish question) Also, why aren't other people running into this here... It should occur with any fast horizontal 2d scroller...

Edit: I'm googling directFB =)

---

### Post by 23meg on 2005-10-12
i'm suffering from low 2d performance in gnome, and vertical tears at the edges of windows when dragging them. the latter seems to be a vertical sync problem. i'm using a laptop with a nvidia gforce go6200 graphics chip, via the pci express bus, so it shouldn't need to use any agp modules/drivers. but when i type "lsmod | grep -i agp" i'm getting the following:

> intel_agp              23164  1
agpgart                34792  2 nvidia,intel_agp


could this be the cause?

---

### Post by shawn on 2005-10-12
I realise that the MAME problem above is old, but I thought this should be mentioned for anyone else that sets up MAME.

MAME will always tear at varying degrees on monitors. The reason being that arcade monitors run at 56hz and MAME emulates this. Setting your refresh rate to 60hz is the closest you will get to perfect. There are custom builds of MAME which up the rate to 60hz on the games for you, I think advancemame will do it. I had all this trouble setting up a MAME cabinet a few years ago (in windows).

Change the refresh rate to 60hz and you should see an improvement. Also not all arcade games run at 56hz so some games will tear more than others.

23meg, sorry this doesn't help you, I have no idea about your problem. Its worth mentioning though that I also had the window tearing in gnome, so i turned off 'show window contents while dragging'.

---

### Post by Feirax on 2005-10-12
I'm also experiencing the exact same tearing issue.  I'm running with the nvidia driver installed via synaptic and the appropriate monitor modes in my xorg.conf.  I believe the only non-std option I have set for my video driver is renderaccel.  

Normally I would just turn off show window contents while dragging, but it bugs me that this works fine on my box when it's booted into FC4 using the same theme (clearlooks).  

-F

---

### Post by Curlydave on 2005-10-12
I've had no luck getting vsync to work with ATI in Linux. Boo. I'm a vsync whore in Windows and don't run anyting without it.

Don't even think about TB. waayyy too advanced at this point. :???:

---

### Post by 23meg on 2005-10-17
i've started using xcompmgr just to remedy the inferior 2d performance i get in gnome. no more tearing, at least!

---

