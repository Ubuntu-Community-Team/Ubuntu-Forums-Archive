---
title: "Sound Problem ... Help!"
date: 2005-02-14
forum: Desktop Environments
---

### Post by smx on 2005-02-14
Help! Mouse movement, particularly scrolling, produces loud clicks and squeals when I play a music file.

 Just switched from Slackware, where I used gdm for the last year with no problems. I'm certain this is not a hardware issue. I'm using the same drivers that I always have, (ensoniq)

Is this a GStreamer issue? 

ogg123 and mpg123 work fine from the command line. I'm using alsa, but OSS produces the same result.

Is this a simple configuration issue? What happens if I uninstall gstreamer? 

Apologize if this has been addressed elsewhere here. I looked, but didn't find it.

Any help would be greatly appreciated! The ubuntu dist is great, but this relatively small problem is a major obstacle at the moment. ANY ideas would be welcome, as I'm about ready to go back to Slackware  ....

---

### Post by kamstrup on 2005-02-15
I've never heard of prob's like these before, but gstreamer might be at work here... but honestly, I don't know.

Uninstalling gstreamer should be perfectly doable. You'll just have to pull in totem-xine or mplayer, xmms what ever to play your multimedia (unless mph123 floats your boat :-) )...

You'll find most in Universe - except mplayer. For mplayer there's a good howto, somewhere in the HOWTO-section (surprise!)...

Good luck.

WAIT! STOP! LOOK HERE!
--------------------------------------
Don't uninstall gstreamer! I just realized that it would uninstall most of GNOME with it. Just try and install the xine stuff and what else together with gstreamer.

---

### Post by Buffalo Soldier on 2005-02-15
smx,

This is just a wild guess, but it could be something along your graphic card or Xserver interupting your soundcard.

Hopefully someone more knowledgable can point you towards the right direction.

---

### Post by smx on 2005-02-15
Thanks for trying. I suspect that you're on to something with he idea that x is  interrupting something, though I also think that gdm could be the culprit. 

I've edited XF86Config to use different mouse configurations, but no success so far. 

Isn't there a general ubuntu configuration tool? 

How do I configure gdm to stop capturing the mouse?

---

### Post by uboltun on 2007-12-26
I started to have the same problem when I put an old pci Matrox card on my desktop (my NVidia had a broken fan) Every time I move mouse or play video there is a clicking sound as if any refresh of the screen interfere with sound. The music plays fine with xmms when I switch to console (ctrl+alt+f1). Tried to change pci slots for video card but no success. 
lspci produces:
0000:00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
0000:02:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
0000:02:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
0000:02:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
0000:02:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:02:0d.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)

---

