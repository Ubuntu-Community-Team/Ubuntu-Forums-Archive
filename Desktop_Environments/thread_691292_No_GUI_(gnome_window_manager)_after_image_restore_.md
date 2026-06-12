---
title: "No GUI (gnome window manager) after image restore to different hardware"
date: 2008-02-08
forum: Desktop Environments
---

### Post by ocr14a on 2008-02-08
Hi All.  :confused: 
I have been successfully using Gusty on a Dell OptiPlex GX280 desktop computer for a while now, and wanted to get it going on my Dell Latitude D420 notebook computer. 

So, I tried what I have done many times with other OSes (even with this same install over to another kind of laptop)....which is Acronis TrueImage....save image from the GX280 desktop, and then restore it to the D420 notebook. 

However, on this machine, when it boots, it only gets as far as the commandline. 
I can log in and even use the network (i.e. ping google, etc), but there's no GUI. 

I'm assuming it's a driver issue, but I have no idea where to go next. 

Oh ya...I tried starting gnome-window-manager (or whatever) and it failed with no error message. 

Also, I can boot just fine to the CD. 

Any ideas? 
...like, is there such thing as doing a 'repair install' where it will take a look at all of the drivers and fix whatever needs fixing?   :) 

steven

---

### Post by taurus on 2008-02-08
You need to reconfigure the X server with the new hardware, graphic card & monitor, again.

Log in and run

```
sudo dpkg-reconfigure xserver-xorg
```
When you are done with it, see if you can start it with

```
startx
```

---

### Post by ocr14a on 2008-02-08
Thanks, Taurus. 

I did that (not sure if I chose all of the correct options - tried to go defaults as much as possible), and now I have GUI.   Yeah!!  :) 

However, I am having difficulty getting the full screen resolution that I'm supposed to be able to get. 

Onboard graphics:
Intel Corporation
Mobile 945GM/GMS, 943/940GML 
Express Integrated Graphics Controller

Monitor: 
Dell E248WFPb 
Native Res: 1920x1200

Any ideas? 

steven

---

### Post by Keith Hedger on 2008-02-08
You may need to edit /etc/X11/xorg.conf by hand and look for a section like ```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x540"	"720x400"	"640x480"
	EndSubSection
EndSection
```

and add the resolution manually

---

### Post by ocr14a on 2008-02-08
So, can I just add the resolution to the screen section and not put anything in the other section (the one with all of the crazy numbers)?

---

### Post by taurus on 2008-02-08
Also, which Driver do you use in /etc/X11/xorg.conf for your Intel graphic controller?

---

### Post by Keith Hedger on 2008-02-09
Yes sorry i wasn't clear just add the resolution to the "mode" line highest resolution first ( I think the 1st resolution is the default in my case it would be "1280x1024") so just add your max res there, I would take a backup of your xorg.conf file first so that if anything goes wrong you can easily put it back the way it was.

---

