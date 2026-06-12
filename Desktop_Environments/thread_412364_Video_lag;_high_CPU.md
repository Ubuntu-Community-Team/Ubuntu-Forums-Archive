---
title: "Video lag; high CPU"
date: 2007-04-18
forum: Desktop Environments
---

### Post by NJC on 2007-04-18
PIII/500Mhz running Ubuntu 6.06. Screenshot taken tonight:

[IMG]http://i18.photobucket.com/albums/b107/Volvo745/Screenshot.png[/IMG]

Part of the lagging video problem is the high CPU usage, The CPU spikes seen above are from ONLY Alt-Tab'ing between windows ... with Thunderbird being the worst offender. 

I have installed BUM and tried to turn off uneccesary processes, changed video depth to 16 but no joy. I understand Xubuntu is a lot less CPU intensive than Gnome but after the effort I have gone through to get this working, I'm sticking with it!

Anything obvious I need to try or is this high CPU use par for the course for a PIII/500Mhz?

---

### Post by voided3 on 2007-05-08
What kind of graphics card are you running? Also, what is the fps reading from the command "glxgears -printfps" (or just "glxgears" if that doesn't work)?

---

### Post by NJC on 2007-05-08
Matrox Millenium G200 8 megs. It's the likely culprit of my screen lag problem. Here's the glxgears output:

787 frames in 5.0 seconds = 157.382 FPS
791 frames in 5.0 seconds = 158.177 FPS
795 frames in 5.0 seconds = 158.875 FPS
797 frames in 5.0 seconds = 159.363 FPS
783 frames in 5.0 seconds = 156.487 FPS
794 frames in 5.0 seconds = 158.690 FPS
771 frames in 5.0 seconds = 154.135 FPS

EDIT:

I wasn't able to use the Framebuffer (?) when I installed video. Relevant info from xorg.conf:

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA G200 AGP"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	VideoRam	8000
	Option		"OldDmaInit"		"True"
EndSection

[...]

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G200 AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	16

---

### Post by rich.bradshaw on 2007-05-08
I would still recommend using Xubuntu on a laptop of that spec, you will likely find that that is lightweight enough to use. Gnome is much more memory intensive...

You can try it by:

sudo apt-get install xubuntu-desktop

then logout of gnome and choose xubuntu from the sessions menu. This will enable you to have both installe, but still have a choice - see if Xubuntu is faster and let us know!

---

### Post by voided3 on 2007-05-08
Yes, installing Xubuntu (or at least the desktop environment) would be a great idea for a 500mhz machine; I ran Xubuntu 6.10 on a 450mhz AMD K-6 III system with 192mb of RAM and it fared quite well for firefox, gaim, XMMS, and abiword usage (it even ran Quake III smoothly at 640x480 :-D ). That computer though had a 32mb nvidia TNT2 64 in it which has significantly more graphics memory than your Matrox card. If you can find drivers for the card, by all means install them, but otherwise I might recommend stepping up the graphics card if at all possible. I have a 64mb nvidia MX440 in a computer with a 713mhz (OCed) intel celeron and it gets almost 2000 fps in glxgears with the nvidia-glx driver in 6.10 (I don't know how that's possible, but hey; I get about 80fps in Planet Penguin!). I'm sure that you could find one for very cheap on ebay or even brand new possibly like this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814143098](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143098)

That would be an excellent upgrade; perhaps you could even find the same card or a similar one for even less on ebay. Otherwise, perhaps there are some more possible xorg tweaks to try that I am not aware of (and definitely try the xfce desktop; I use it on everything, even my faster computers). If you're willing to try something more drastic, you could install Puppy Linux on that comp. I did an HDD install of that on the same K6-III computer above and it's even faster than Xubuntu, and on the celeron comp it flies (Seamonkey browser opens in about one second). The trade off though is that Puppy Linux is great with speed since it uses IceWM and is very easy to setup, but Xubuntu has more of the newer apps and kernel (though I am sure there is a way to change that). Anyway, tweak on!

---

### Post by NJC on 2007-05-18
> **rich.bradshaw said:**
> sudo apt-get install xubuntu-desktop

I ran the code and came up with this. Normally I'd damn the torpedoes but thought I should prolly check:```
WARNING: The following packages cannot be authenticated!
  libwpd-stream8c2a libgsf-gnome-1-113 smbclient

```

Anything to worry about?

---

### Post by NJC on 2008-05-03
Now running Ubuntu 8.04 on an AMD Duron 1.3Ghz. Methinks System Monitor is **VERY CPU **THIRSTY. 68% CPU usage to idle those programs?? The 2nd screenshot was taken right after first, after closing System Monitor and opening Terminal.

EDIT: This seems to be a bug. System Monitor causes high CPU usage in Xorg. See the following:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)
[https://bugs.launchpad.net/ubuntu/+bug/178400](https://bugs.launchpad.net/ubuntu/+bug/178400)

---

