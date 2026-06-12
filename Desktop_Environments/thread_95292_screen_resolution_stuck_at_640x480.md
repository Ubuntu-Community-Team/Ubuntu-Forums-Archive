---
title: "screen resolution stuck at 640x480"
date: 2005-11-26
forum: Desktop Environments
---

### Post by nkostis on 2005-11-26
Hi,
just installed Ubuntu 5.10, and my screen resolution is stuck at 640x480 (painful) with no option for increasing it (i use 1280x1024 in windows). I have an nForce2 m/b using the integrated graphics driver, basically a gforce4-mx440.

I downloaded the graphics driver from nvidia but when run it says that it cannot find ld (which i think is the generic linker --i'm obviously a newbie with linux).

any help would be greatly appreciated...

thanks,
nikos

---

### Post by frodon on 2005-11-26
First i advice you to install the ubuntu nvidia drivers (more easy for a newbie), you can install it with synaptic.
For your resolution problem you will need to put in your xorg.conf file the hsync and vertsync parameters of your screen.

Post here your xorg.conf and give us the exact name of your screen or the vert and horiz. refresh rates written in your screen specification: ```
sudo gedit /etc/xorg.conf
```

---

### Post by nkostis on 2005-11-26
hi, thanks for your answer and sorry for the large post..:

- i tried to install the nvidia drivers but the installer cannot find ld and fails.

- i had tried editing the xorg.conf file, by placing a very specific 1280x1024x85hz configuration which i got from gtf (see below) but the resolution app still only shows one resolution (640x480).

- more importantly (maybe) the device manager window is odd, as it shows the following *two* drivers for graphics:
"
   - nForce2 AGP (different version?)
   - nForce2 AGP
          NV18 [GeForce4MX - nForce GPU]
"
so for some reason sees a second unidentified GPU driver. (could it be the failed installation of the nvidia driver set?

also (this will sound stupid), how do i end the x-session without having to leave linux? it seems Gnome will only let me logout/login, reboot, shutdown pc. how can i just get to the console with no X running at all (so that i can test changes without rebooting) ?

thanks


xorg.conf file:
-----------------

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Q790"
	Option		"DPMS"
# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 15 9.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744   1024 1025 1028 1075  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"Q790"
	DefaultDepth	24
...
[deleted depths from 1bpp to 16bpp for post, not from real file]
...
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024_85.00" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by frodon on 2005-11-26
When you say "i tried to install nvidia drivers", which one it is ? the ubuntu package or a package coming from the nvidia site.
To end X-session you just need to choose "leave session" when you log_out, Ctrl+Alt+Backspace do also the job but is a little stronger.
Sorry to ask it again but i need to know the exact name of your screen or the horiz and vert. refresh rates which are specified in your screen specification.

---

### Post by nkostis on 2005-11-26
the nvidia driver referred to is the driver set downloaded from nvidia, (NVIDIA-Linux-x86-1.0-7676-pkg1.run)

my monitor is a Hyundai ImageQuest Q790. It supports up to 1280x1024 @ 85Hz:

# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 15 9.36 MHz
Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync

i am sorry if i'm not getting the question.

also, there doesn't seem to be a "leave session" option, only logout / reboot / shutdown / hibernate. Logging out just gets you to the gnome login screen where you can only login/reboot/shutdown...
it also doesn't 'like' ctrl+alt+backspace as it thinks that it's due to a crash.

---

### Post by frodon on 2005-11-26
I have a french version but logout should only quit the sessions and return to the login screen.
Ok, if you are a newbie i strongly advice you to install the ubuntu nvidia drivers because it really easy. type in a terminal the following commands : ```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```insert that in the text file opened : ```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
```Then save the file and do a Ctrl+Alt+Backspace. You should have a menu in Applications -> System Tools -> NVIDIA Settings now.
For your screen resolution modify the monitor section of your xorg.conf file like that : ```
Section "Monitor"
Identifier "Q790"
Option "DPMS"
HorizSync	30-97
VertRefresh	50-150
EndSection
```You should restart xsession after that also.

---

### Post by nkostis on 2005-11-26
ok, that worked..!

THANKS!

nikos

---

### Post by dosed150 on 2005-11-26
how do i get to xorg conf

---

### Post by atoponce on 2005-11-26
xorg.conf is located in /etc/X11.  You can edit the file manually, or you can launch the built-in configuration utility from the terminal:

```
sudo dpkg-reconfigure xserver-xorg
Password:
```

---

### Post by frodon on 2005-11-26
[QUOTE=dosed150]how do i get to xorg conf[/QUOTE]Type in a terminal : ```
sudo gedit /etc/X11/xorg.conf
```If you don't use the sudo command before gedit you will not be able to edit the file.

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```
(BTW, This is the guided way into xorg.conf)

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

### Post by zeusdo on 2006-08-02
This is an excellent thread, because I am having the same problem, only difference, I have an ATI card. I installed Ubuntu last night for the first time and was not able to change the screen resolution from 640x480, it did not give me any other options. I did run --  sudo dpkg-reconfigure xserver-xorg ---   and when it got to the screen resolution, all the choices I would want were already checked, but then I still had no other choices when trying to change the screen. Does any of this make sense?

---

### Post by zeusdo on 2006-08-03
Well that's it, I'm giving up on Ubuntu. Over the last few months I have read so many good things about it I figured I would give it a try. I have tried everything there is to try over the past two days and my screen resolution is still 640x480, I should say it was, now I can't even boot up. It is a shame that something as simple as changing the screen resolution is this difficult. I guess I'll be a Windows user for ever, I have not had one single problem with Vista bata so far.

---

### Post by zeusdo on 2006-08-12
I finally got it work, thanks to this thread"http://www.ubuntuforums.org/showthread.php?t=190133"
all is good in the world now.:D

---

