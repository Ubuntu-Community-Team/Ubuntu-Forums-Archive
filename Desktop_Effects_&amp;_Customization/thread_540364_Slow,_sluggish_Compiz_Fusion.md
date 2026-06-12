---
title: "Slow, sluggish Compiz Fusion"
date: 2007-09-01
forum: Desktop Effects &amp; Customization
---

### Post by petit.padavoine on 2007-09-01
I recently installed Compiz Fusion on a (reasonably) old desktop and it's pretty sluggish. For instance, zooming back in from the cube takes about 10 seconds all in all. Switching windows using Cover Flow or even just the Alt+Tab switcher takes at least 3 seconds, and some plugins (such as Water Effect) just don't start.

```

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

```

It's an Ati Radeon 7000 graphics card, so although it's not top of the line, I think it should run smoothly enough.

The processor is a Pentium 4, clock speed is around 1 Ghz and RAM is 512MB.

I'm wondering if the slowness is entirely due to the hardware (which I doubt, as it IS reasonably good hardware and Compiz Fusion is reported to run pretty well with similar specs) or if some of it is due to misconfiguration.

The [official Compiz page about ATI cards](http://compiz.org/ATI) recommends adding the following lines to the Device section of xorg.conf to boost performance:

```

Option		"DRI"			"true"
Option		"ColorTiling"		"on"
Option		"EnablePageFlip"	"true"
Option		"AccelMethod" 		"EXA"
Option		"XAANoOffscreenPixmaps"
Option		"RenderAccel"		"true"
Option 		"AGPMode" 		"x"
Option		"AGPFastWrite"		"on"

```

I found that "AccelMethod" "EXA" made CF crash so after searching on the net, I changed that to "AccelMethod" "XAA".

It's still as slow.

I'm using the default driver that was installed with Ubuntu, so I guess it's the open-source r200 driver. The restricted drivers manager says I don't need any additional drivers.

The Compiz Fusion I have is from Trevino's repository.

I'm launching Compiz Fusion using fusion-icon, which I compiled from the git repository source.

Any help?

Is it the hardware?

Can I add some additional configuration to my xorg.conf?

Should I try the fglrx (proprietary) driver?

Should I try another way of launching CF?

Any feedback would be appreciated.

Thanks

---

### Post by petit.padavoine on 2007-09-01
Bump.

This is really hindering my work on the PC, and I would like to keep CF.

Any help?

---

### Post by petit.padavoine on 2007-09-02
Bump.

I wanted to try XGL to see if it would speed up things, so I installed fglrx, and ran dpkg-reconfigure xorg.conf, but then gdm wouldn't start because X didn't recognize my screen.

So I reverted to my original xorg.conf (with the open-source driver), and for some reason, I didn't have 3D acceleration anymore.

Oh well.

I reinstalled Feisty :D.

I'm upgrading to Gutsy to see if the integrated Compiz Fusion runs any better, but it's a lost hope...

Any tips, any help, anything?

---

### Post by kellemes on 2007-09-02
You need fglrx + xgl to get fine performance with this card.
AIGLX will not work with this card, instead use XGL.

For this you need to include the following section in xorg.conf
Section "Serverflags"
  Option "AIGLX" "off"
EndSection

also you need to include
Section "Extensions"
  Option "Composite" "Disable"
EndSection

Next time you need to post **/etc/X11/xorg.conf** and **/var/log/Xorg.0.log** so we can help.

Watch the stickies in the forums, there is a lot of info about this..

Edit: you need to search this forums for the combination fglrx + xgl since you need to get xgl running for this to work.

---

### Post by petit.padavoine on 2007-09-02
Okay, I was wondering whether I should switch, but as posted above, switching to fglrx miserably failed...
I followed the [Ubuntu Documentation page](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html) about switching to fglrx, but as stated above, this miserably failed, probably because I don't know how to correctly configure Xorg...
I would install fglrx using the restricted drivers manager if I could, but when I launch it it tells me my hardware doesn't need any restricted drivers...

---

### Post by Forlong on 2007-09-02
> **petit.padavoine said:**
> I would install fglrx using the restricted drivers manager if I could, but when I launch it it tells me my hardware doesn't need any restricted drivers...
That's because the fglrx driver unfortunately doesn't support your graphics card:
> The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as ATI FireGL 8700 and later products. We do not currently plan to include support for any products earlier than this.

---

### Post by kellemes on 2007-09-02
> **Forlong said:**
> That's because the fglrx driver unfortunately doesn't support your graphics card:

Sorry I didn't know this..

---

