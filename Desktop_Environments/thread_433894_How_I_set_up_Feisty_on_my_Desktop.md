---
title: "How I set up Feisty on my Desktop"
date: 2007-05-05
forum: Desktop Environments
---

### Post by rfrey74 on 2007-05-05
I chronicled my experience setting up Feisty on my home built desktop in the hope that others may find it useful.  So, without further ado, here is how I set up Feisty on my home built desktop

Setting up Feisty on a home built Desktop

Hardware Profile

$ cat /proc/cpuinfo

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 8
model name	: AMD Athlon(tm) XP 2400+
stepping	: 1
cpu MHz		: 1997.033
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips	: 3997.13
clflush size	: 32

$ lspci

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:08.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
01:0a.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
02:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

Partitioning

/dev/hda1	70 GB	NTFS	C:\
/dev/hda2	10 GB	EXT3	/
/dev/hda3	117 GB	XFS	/home
/dev/hda4	3 GB	SWAP	swap

Post Installation Setup

$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo apt-get install sun-java6-jdk

Drivers

I have an ATI Radeon 9550, so I Installed the graphics accelerator driver for Radeon cards.
$ sudo apt-get install xorg-driver-fglrx
$ sudo restricted-manager
Check the "Enabled" box next to ATI accelerated graphics driver.
I plan on installing tvtime, and tvtime won't launch properly unless I alter the X11 configuration file as follows
$ sudo gedit /etc/X11/xorg.conf
Scroll to the Section named "Device" and add the following:
Option		"VideoOverlay"	"on"
Option		"OpenGLOverlay	"off"
Save and close gedit.

Multimedia
First, I set up the 3rd party repo that has w32codecs and libdvdcss2.
$ sudo gedit /etc/apt/sources.list
Add the following to the end of the file
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 
Save and close gedit
$ sudo wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
$ sudo apt-get update
Gnome uses gstreamer for its media support.
In my experience, gstreamer causes video delay when playing video files, and gstreamer also has no DVD menu support.
Therefore, I installed (the far superior IMHO) xine version of totem along with the extra codecs for xine.
$ sudo apt-get install msttcorefonts flashplugin-nonfree totem-xine libxine-extracodecs tvtime
I installed the remaining gstreamer plugins for those media applications that don't use the xine library.
$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-pitfdll
$ sudo apt-get gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
Then I installed the DVD decoding library along with the codecs for Windows media files.
$ sudo apt-get install w32codecs libdvdcss2
On my desktop, I have an on-board audio card as well as a PCI audio card.
Feisty selects the on-board card as default, and the Sounds interface in Gnome doesn't do anything when I select a different card as default.
Therefore, I had to manually select the default card.
$ alsamixer
The card listed in the mixer is the current default.  If this is not the desired default card, follow the procedure below.
Determine available sound cards.
$ cat /proc/asound/cards
My desired card was card number 1.
$ gedit ~/.asoundrc
Type the following into gedit:
pcm.!default {
	type hw
	card 1
}
ctl.!default {
	type hw
	card 1
}
Save and close gedit.

---

### Post by neouser99 on 2007-05-05
coolio, congrats. might i offer a suggestion for an update, go through the list of drivers and programs you installed a briefly list why you installed them. that way if someone knew, like yourself, stumbles upon this he will know why he needs them.

just for example, not everyone has an ATI gfx card, there for ```
sudo apt-get install xorg-driver-fglrx
``` won't do anything for them.

but, that is not to be taken as a flame, just some constructive criticism 

-neo

---

### Post by rfrey74 on 2007-05-06
Update made.  I hope it is more useful with the annotation.

---

### Post by rfrey74 on 2007-05-26
I have updated the first post with a better way to install some of the multimedia applications.

---

### Post by Bakon Jarser on 2007-08-29
Thanks.  I was really missing having dvd menus.

---

