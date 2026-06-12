---
title: "Xorg uses 100% of CPU (Ubunto performance worse than WinXP)"
date: 2005-10-26
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-26
Tasks:  70 total,   2 running,  68 sleeping,   0 stopped,   0 zombie
Cpu(s): 98.0% us,  1.3% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.7% si
Mem:    256848k total,   249100k used,     7748k free,     2640k buffers
Swap:   248996k total,   166584k used,    82412k free,    53556k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7174 root      25   0  115m  29m 4420 R 92.8 11.9 576:21.61 Xorg


This is the 'top' result in my machine. I was only running XFCE and aMule for the last 20 hours and then.. BOOM, Xorg uses 92.8% of my CPU. Xorg do not use less than 80% of CPU after 10 hours running. My processor is a SEMPROM 2800 (2.4gHhz). My swap is status is 163MB used from 243mb allocated. I get even a worse performace if I use the default Ubuntu interface, gnome.

Why Xorg is using so much CPU ? How can I solve this ? Even if I left the computer untouched, after 10h I get this bad performace. I've never experienced it with Windows XP. I've already let my machine running emule for 5 days with no significant loss of performace comparing to Ubuntu.

Its is unbeliveble for me that I will have to install Windows XP to get my box running for more than 10h because Ubuntu can't handle that. My video card is a NVIDIA and I've downloaded the NVIDIA drivers thru aptitude.

Any suggestions ?

---

### Post by Casey on 2005-10-26
Xorg is only using 2% of my CPU (which is underclocking itself to 1ghz at the moment).

Are you using any xorg extensions other than what ubuntu ships with in xorg?  Also what graphics driver are you using?  -- ATI's binaries by any chance?  I wonder if a bad graphics driver could do this.

---

### Post by kurtkraut on 2005-10-26
I've found the following 17 posts reporting the same problem. None of them has a solution:

[http://www.ubuntuforums.org/showthread.php?t=80435&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=80435&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=77168&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=77168&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=76719&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=76719&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=64676&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=64676&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=75089&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=75089&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=74819&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=74819&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=74772&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=74772&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=74711&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=74711&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=74212&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=74212&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=68615&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=68615&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=66952&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=66952&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=59840&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=59840&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=43930&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=43930&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=42806&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=42806&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=20440&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=20440&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=17800&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=17800&highlight=CPU+Xorg)
[http://www.ubuntuforums.org/showthread.php?t=17842&highlight=CPU+Xorg](http://www.ubuntuforums.org/showthread.php?t=17842&highlight=CPU+Xorg)


They all have in commom:

1- It happens on Breezy and never happened in Hoary
2- The machine is almost untouched
3- The Xorg CPU usage is constant, with no intervals

They do not have in common:

4- Video card (most if then are using NVIDIA or RADEON)
5- Interface (it happens in gnome or XFCe for instance)
6- Computer hardware (fast machines and slow/old machines are having the same problem)

Is there any Ubuntu geek that could solve this mistery ?

Thanks in advance

---

### Post by kurtkraut on 2005-10-26
[QUOTE=Casey]Xorg is only using 2% of my CPU (which is underclocking itself to 1ghz at the moment).

Are you using any xorg extensions other than what ubuntu ships with in xorg?  Also what graphics driver are you using?  -- ATI's binaries by any chance?  I wonder if a bad graphics driver could do this.[/QUOTE]


Besides NVIDIA driver, downloaded from ubuntu's repository, there was no changes in Xorg. It is working as it was shipped.

---

### Post by angkor on 2005-10-26
Do you have RenderAccel = true in your xorg.conf? It crashed my X repeatedly with Xorg taking +/- 95% of the cpu.

After deleting this line it hasn't crashed yet.

Btw, post your /etc/X11/xorg.conf anyway to see what you have in there.

---

### Post by kurtkraut on 2005-10-26
Here is my xorg.conf: [http://www.kurtkraut.net/xorg.conf](http://www.kurtkraut.net/xorg.conf)

---

### Post by angkor on 2005-10-27
Try commenting out 

Load dri
Load glx

in the modules sections by putting a # before the line.

---

### Post by LittleReinhart on 2005-10-30
Hey,

[QUOTE=kurtkraut]I've found the following 17 posts reporting the same problem. None of them has a solution:

They all have in commom:

1- It happens on Breezy and never happened in Hoary
2- The machine is almost untouched
3- The Xorg CPU usage is constant, with no intervals

They do not have in common:

4- Video card (most if then are using NVIDIA or RADEON)
5- Interface (it happens in gnome or XFCe for instance)
6- Computer hardware (fast machines and slow/old machines are having the same problem)[/QUOTE]

If I read all the posts about this subject, it seems like I onely have minor problems, but still, I would like to explain my problem, to help the experts to look for a sollution for us all.

My system:
Amd64 +3000, 2Gb sdram, MSI k8n Platinum sli with a very basic vga-card NVIDIA Corporation NV36 [GeForce PCX 5750] (dual head with 128Mb) (I never play computergames... so I don't nead a havy card)
Ubuntu 5.10, with Enlightenment 0.16.6 (gnome and kde are also installed, but I onely use enlightenment with the apps from the other two).

Since the beginning, when I scroll in firefox (and some other programs like OpenOffice2), it doens't scroll smoothly.
I find this realy strange, definately if you know that I could watch 9 movies with mplayer without a problem (with 10 movies the cpu-load is at 100% and the movies slow down).
About a month ago, I got an extra monitor. (see my xorg.conf below). (now I can onely watch 4 movies at the same time)

Yesterday I was uploading some files to a laptop. The transfer speed was extremely slow (<1Mb/s for a 100MB network), and I noticed my cpu-load was at 100% (xorg was using +80% cpu).
I aborted it, rebooted, started it again, and it went fine then (cpuload for xorg <30%)

This morning, I had about 10 programs running (thunderbird, gaim, xmms, a terminal,gnome-system-monitor and 5 bittorrents) with a total cpu-load around 30%, I was chatting with gaim and I resized the chatbox.... my cpu-load went up to 100% and my ubuntu totaly froze!!! (normaly if that happens (only when I'm doing a lot at the same time) I press "ctrl + alt + F2" wait a few seconds and then press "alt + F7" , and everything works again, but now even that won't work. I had to push the computerbutton (twice, cus the first time I didn't even get the login-screen).

Now everything works fine, cpu-load from 1% to 4% (when I scroll inside this window (firefox), the cpu-load is about 3% to 35%, but it still doesn't scroll smoothly).

So, I hope this helps the developpers to solve the problem, for me personally it's not urgent (as long as it stays with these two cases).

I also didn't knew this problem with ubuntu 5.04 (but then I didn't have dual-screen).

If you nead more information, just ask.

Greetings,
Reinhart


```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce PCX 5750] 0"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Screen		0
	Option		"NoLogo"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce PCX 5750] 1"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
	Screen		1
	Option		"NoLogo"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor 0"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

Section "Monitor"
        Identifier      "Generic Monitor 1"
        Option          "DPMS"
        HorizSync       30-115
        VertRefresh     50-160
EndSection



Section "Screen"
	Identifier	"Default Screen 0"
	Device		"NVIDIA Corporation NV36 [GeForce PCX 5750] 0"
	Monitor		"Generic Monitor 0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Default Screen 1"
        Device          "NVIDIA Corporation NV36 [GeForce PCX 5750] 1"
        Monitor         "Generic Monitor 1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1400" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen 0" 0 0
	Screen		"Default Screen 1" LeftOf "Default Screen 0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
	Option "Xinerama"
EndSection
```

---

### Post by Qrk on 2005-10-30
I'd try 

sudo dpkg-reconfigure xserver-xorg

change the default driver from nv to vesa. (make sure you write down everything you've changed so that you can restore it if it doesn't work)

---

### Post by TheJoker on 2005-11-30
Was there ever any results to this? I'm having similar problems. When I initially installed Kubuntu I had to disable powernowd and add a few parameters to the boot up parameters.
Now I got a new kernel (2.6.12-10-amd64-generic) and it started again, I've also updated to KDE3.5 but I don't think that's got much to do with it...

---

### Post by AndersAA on 2005-11-30
try xrestop (top for X), it could be X isn't really using that much, but some software in shared memory is causing it.

---

### Post by mym on 2005-12-14
Same problem here.
Sometimes Xorg starts to use 50-70% of CPU.
Killing Xorg doesn't solve the problem, I have to reboot my laptop :(
My hardware: Acer Aspire 1694WLMI (Centrino 2Hz, ATI X700 128Mo).
My Linux: Ubuntu Breezy, then I installed Kubuntu KDE packages, but had the same problem with KDE :???:

---

### Post by Paulus on 2005-12-14
I have the exact same problem, for me I have to restart x, but that hard locks my system these days with the new nvidia driver!  So I have to reboot, I am running KDE 3.5 installed from ubuntu, with kompmgr,  no solution just adding to the thread!


p.s this needs to be sorted!

EDIT: This is kompmgr problem-- see below

---

### Post by AndersAA on 2005-12-14
your running compmgr, that's your problem, this is not supported at all and known to have stability issues.

---

### Post by Paulus on 2005-12-14
I've never had these problems even with Xcompmgr, I am aware people have mentioned this in the past, but recently I have seen complaints regarding this issue dwindle, especially with the 81 nvidia drivers and Kompmgr ( considered to be more stable).  I'll entertain and disable kompmgr and let u know in a day or so!

---

### Post by AndersAA on 2005-12-14
[QUOTE=Paulus]I've never had these problems even with Xcompmgr, I am aware people have mentioned this in the past, but recently I have seen complaints regarding this issue dwindle, especially with the 81 nvidia drivers and Kompmgr ( considered to be more stable).  I'll entertain and disable kompmgr and let u know in a day or so![/QUOTE]

try disabling both renderaccel and composite and see if it's stable.

---

### Post by Paulus on 2005-12-16
hey, turns out you were right, sorta.  I think it's when u use kompmgr with only windeco enabled, it's pretty unstable tbh.  Running standard kompmgr now and it's rock stable- touch wood!

---

### Post by jannol on 2005-12-16
I think it is the nvidia driver, if you can stand a slower performance overall, specially games so turn off composite glx and dri in xorg.conf, that fix/helps, however I am running xcompmgr and it seems to work fine for me now since I installed nvidia 7676 drivers and put xcompmgr to autostart from the sessions start programs. Memory is building up but around 800-900 megs it kinad restarts or something and then it is about 200 megs total, I noticed it in a small 0.2 sec hang when I watched a movie and had to check :P

btw I have 1 GB ram

[http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)

---

### Post by Paulus on 2005-12-24
NU Nvidia driver fixes all!  Thanks nv :D

---

### Post by mym on 2006-01-07
[QUOTE=jannol]I think it is the nvidia driver, if you can stand a slower performance overall, specially games so turn off composite glx and dri in xorg.conf, that fix/helps, however I am running xcompmgr and it seems to work fine for me now since I installed nvidia 7676 drivers and put xcompmgr to autostart from the sessions start programs. Memory is building up but around 800-900 megs it kinad restarts or something and then it is about 200 megs total, I noticed it in a small 0.2 sec hang when I watched a movie and had to check :P

btw I have 1 GB ram

[http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)[/QUOTE]
I have ATI drivers.
I have advanced in the diagnostic: it only happens when I let iddle my laptop some minutes. This should be related to a sleep status of Xorg...
I have the last Breezy ATI drivers.

---

### Post by zappa86 on 2006-01-07
My xorg farts too. Whenever I try to make a large selection box (click 'n drag) and select many icons on my desktop my CPU jumps up to 100% and it stays there for a sec or 2 before going down. I'm running a nvidia 6800.

---

### Post by eetfuk on 2007-06-18
This somewhat happends on my Amilo Laptop...
But only when running certain applications like firefox, but it depends on content showing.
And Guitar Pro 5 trought wine... Anny suggestions?

---

