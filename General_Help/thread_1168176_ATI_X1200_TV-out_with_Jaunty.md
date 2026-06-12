---
title: "ATI X1200 TV-out with Jaunty"
date: 2009-05-23
forum: General Help
---

### Post by ugm6hr on 2009-05-23
I have been trying to get my TV-out (S-Video) work with Jaunty.

Hardware details:

lspci
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
```

lshw
```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690 [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64

```

The Mobo is an AMD 690G chipset, which I chose specifically for TV-out capacity in an all-in-one board.

I have had Hardy working fine from a graphics viewpoint, but wanted to upgrade for improved wifi.

Unfortunately, the ATI Catalyst 9.3 fglrx driver which I need no longer works with Jaunty, and my card is (apparently) unsupported with 9.4.

I found 2 alternative drivers for me to use: ati and radeonhd.

The default ati does not work at all on my system; starting X complains about being unable to detect my settings, and then offers to let me manually set things or use the safe graphics (vesa) mode.  Manually configuring xorg as per [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) does no better.  The ati driver apparently works with TV-out, but I can't get it to work at all.

radeonhd apparently does not have TV-out working yet, but works fine with a monitor.

Anyone got any better ideas?  The best solution would be to use fglrx, which I know has worked (with Hardy).

---

### Post by ugm6hr on 2009-05-24
Found lots more links, but nothing has changed: the -ati driver will not display anything; radeonhd does not support TV-out; fglrx doesn't support X1200.

However, there are plenty of reports about the -ati driver working, with moderate 3D support (I only need 2D).  Shame I can't get it to do anything.

I get a graphical error message after splash screen (with -ati driver, and also with LiveUSB):
> **Ubuntu is running in low-graphics mode**
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

[http://pkpatel88.wordpress.com/2009/03/26/how-i-got-tv-out-to-work-with-ati-x1200-without-fglrx/](http://pkpatel88.wordpress.com/2009/03/26/how-i-got-tv-out-to-work-with-ati-x1200-without-fglrx/)
[http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html](http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html)

Anyone else with a X1200 who could supply a sample xorg.conf to me?  The default complains about being unable to detect screens and cards etc before offering the safe mode and personal debugging.  Multiple xorg.conf edits guided by the error logs ends in: unable to find any screens.  I tried to completely remove the fglrx driver (installed by envyng), but I don't think it is a problem of interaction, since it never booted correctly even the first time (which prompted by trial of envyng).

---

### Post by ugm6hr on 2009-05-24
Only way I have managed to get this to work is with the vesa driver, which I didn't even realise had TV-out support until today!

I removed the ati and radeon and fglrx drivers first:
```
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```

My new /etc/X11/xorg.conf

```

Section "Device"
	Identifier	"Card0"
Driver "vesa"
Option "AGP" "1"
Option "ConnectedMonitor" "TV"
Option "TVStandard" "SVIDEO"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
HorizSync 30.0-50.0
VertRefresh 60
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "800x600"
EndSubSection
EndSection
```

While the video performance for is not perfect, it is a good enough solution to keep my HTPC on Jaunty for now.

Thanks to schruthensis for pointing me in this direction: [http://ubuntuforums.org/showthread.php?t=1149615](http://ubuntuforums.org/showthread.php?t=1149615)

---

### Post by ugm6hr on 2009-05-27
> **ugm6hr said:**
> radeonhd apparently does not have TV-out working yet, but works fine with a monitor.

I have been asked to explain I achieved this in a PM.

I did not test the radeonhd driver extensively, but its 2D performance seemed fine for general desktop use.

I simply followed the advice here: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

