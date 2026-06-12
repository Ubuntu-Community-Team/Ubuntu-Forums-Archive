---
title: "Display Problems, Ubuntu 8.10"
date: 2009-03-25
forum: General Help
---

### Post by drewbacca on 2009-03-25
Hello, I have posted this before however I lost that post after some time away and I couldnt find it. I am hoping someone can help me with this problem.

I recently convinced my friend to switch to Linux from windows. After he agreed I went to work installing Ubuntu for him. His system has an NVida Geforce 8600 GT. He also has a 22 inch monitor. After installation I got a warning saying I needed to run the machine in Low Graphics mode. I assumed this was because NVida's drivers do not come with Ubuntu. I was correct and installed the drivers.

Next boot up, I did not get the same warning which was good but I couldnt set the display resolution higher than 640x480. I looked at the xorg.conf and saw it was because xorg did not identify the monitor so I manually entered in the details based on what the manufacturer said the monitor used on their site.

I rebooted, hoping that it would fix the problem. As I logged in, I got no error messages which I assumed meant that the changes took. I was wrong. I still can not set his resolution higher than 640x480 despite the fact I manually changed xorg.conf and have the drivers for the video card.

I made sure, and checked my software sources where all correct (and they are)... not that I am sure that helps but it was what I was told to do last time (and it didn't help then either.)

This is my current xorg.conf:

```

Section "Screen"
	Identifier "Default Screen"
	Device "Default Device"
	Monitor "CHIMEI CMV 221D"
	DefaultDepth 24
	Option "RenderAccel" "True"
	Option "AllowGLXWithComposite" "True"
	Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth 1
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Monitor"
	Identifier "CHIMEI CMV 221D"
	HorizSync 30.0 - 82.0
	VertRefresh 56.0 - 76.0
	Option "DPMS"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

What am I doing wrong? How do I fix it?

---

### Post by norwoods on 2009-03-25
rename /etc/X11/xorg.conf to something else.

to generate a new /etc/X11/xorg.conf, run sudo nvidia-xconfig 

reboot

if you need to, you get a command line by starting Applications-->Accessories-->Terminal
start:
gksu nvidia-settings

try to set resolution here

---

### Post by drewbacca on 2009-03-27
Ok, I tried this and still could not set my resolution higher than 640x480.

---

### Post by decoherence on 2009-03-27
what method did you use to install the nvidia drivers?

---

### Post by drewbacca on 2009-03-27
> **decoherence said:**
> what method did you use to install the nvidia drivers?


There was an option for third party drivers in the drop down menu, which I used to grab the drivers for the video card.

---

### Post by Mattkb on 2009-03-29
Sorry to steal the topic, but I'm having a similar problem. I'm completely new to this though, and I don't really have any idea what I'm doing at this point.

Anyway, as far as I can tell, I tried to upgrade my video card driver. I have a nVidia GeForce 7900 GTX (or something along those lines), and just installed Ubuntu 8.10 a few hours ago. It worked fine, except I couldn't set my resolution any higher than 800x600.. After trying to install/upgrade the driver (I can't recall version or anything, but it *was* the recommended one), I keep getting a "Cannot Display This Video Mode" after it all loads.

I can't even get to my desktop, or whatever. I figured I'd see if anyone here could help me, and if now, I'll just try reinstalling it all from the CD.

Cheers
- Matt.

PS: If you **can** help me fix this, please explain it in a way even I could understand, if possible. :P Much thanks in advance.

---

### Post by drewbacca on 2009-04-01
> **Mattkb said:**
> Sorry to steal the topic, but I'm having a similar problem. I'm completely new to this though, and I don't really have any idea what I'm doing at this point.

Anyway, as far as I can tell, I tried to upgrade my video card driver. I have a nVidia GeForce 7900 GTX (or something along those lines), and just installed Ubuntu 8.10 a few hours ago. It worked fine, except I couldn't set my resolution any higher than 800x600.. After trying to install/upgrade the driver (I can't recall version or anything, but it *was* the recommended one), I keep getting a "Cannot Display This Video Mode" after it all loads.

I can't even get to my desktop, or whatever. I figured I'd see if anyone here could help me, and if now, I'll just try reinstalling it all from the CD.

Cheers
- Matt.

PS: If you **can** help me fix this, please explain it in a way even I could understand, if possible. :P Much thanks in advance.

Lets see if I cant help you... the first thing I want you to do is find out which driver. Just go to administration-third party drivers and it should tell you which driver you have.

Second, I want to see your xorg.conf file. In a command line type: ```
gedit /etc/X11/xorg.conf
```

Copy everything in the file and paste it here.

---

### Post by Mattkb on 2009-04-01
Sorry, mate. Thanks for the reply, but a friend of mine already helped me get it fixed.

Cheers,
Matt.

---

