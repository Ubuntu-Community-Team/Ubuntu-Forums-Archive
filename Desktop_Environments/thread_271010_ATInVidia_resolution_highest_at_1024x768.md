---
title: "ATI/nVidia resolution: highest at 1024x768"
date: 2006-10-04
forum: Desktop Environments
---

### Post by summersab on 2006-10-04
I've done several installs on several different computers. One has an ATI x600 card. Another has an nVidia. Yet another has a S3 Savage. All but the Savage have 3D acceleration. I got the ATI and nVidia drivers from the repositories and I get several thousand fps in glxgears. Even Beryl Compiz works.

That said, none of my installs will give resolutions higher than 1024x768. Some people on the forums claim that after installing, they get the highest resolutions set up by default. Not me. I have done dpkg-reconfigure xserver-xorg, but choosing different resolutions there wouldn't let me select a higher resolution in Preferences. I have done the whole aticonfig --initial thing and fiddled with xorg.conf numerous times on all three machines. No matter what I do, the highest resolution I can choose in the Screen Resolution section of Preferences is 1024x768. Also, I'm using LCD monitors, so H/V refresh rates and frequencies should not present a problem. What do I do? Below is the xorg of my ATI machine (pertinent parts)

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor    "FPD1500"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768"
	EndSubSection
EndSection

---

### Post by herrdoktor330 on 2006-10-04
> **summersab said:**
> I've done several installs on several different computers. One has an ATI x600 card. Another has an nVidia. Yet another has a S3 Savage. All but the Savage have 3D acceleration. I got the ATI and nVidia drivers from the repositories and I get several thousand fps in glxgears. Even Beryl Compiz works.

That said, none of my installs will give resolutions higher than 1024x768. Some people on the forums claim that after installing, they get the highest resolutions set up by default. Not me. I have done dpkg-reconfigure xserver-xorg, but choosing different resolutions there wouldn't let me select a higher resolution in Preferences. I have done the whole aticonfig --initial thing and fiddled with xorg.conf numerous times on all three machines. No matter what I do, the highest resolution I can choose in the Screen Resolution section of Preferences is 1024x768. Also, I'm using LCD monitors, so H/V refresh rates and frequencies should not present a problem. What do I do? Below is the xorg of my ATI machine (pertinent parts)

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor    "FPD1500"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768"
	EndSubSection
EndSection


Dude... all you have to do is add in the other resolutions the card can support manually into your /etc/X11/xorg.conf file. 

Back up your xorg.conf file in case this goes wrong.

all you need to do is:

1) sudo gedit /etc/X11/xorg.conf

2)
```

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor    "FPD1500"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    [COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    [COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    [COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    [COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    [COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    [COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

that's just a resolution I add in... but you can add in your prefered resolutions in that way.

save those changes you made.

3) ctrl+alt+bkspace and log back in.

4) if you check your system > preferences > screen resolution , you should see some new resolutions higher than 1024x768.

Enjoy!

---

### Post by Jordan Meeter on 2006-10-04
Yeah but what about me, who already has 1280x1024 listed in that file, yet cannot make their screen resolution bigger than 640x480? :p

---

### Post by sefs on 2006-10-04
Adding resoultions to conf file does not work for everyone.  There is a thread on here that suggest the use of the modline (i think its spelt like that) directive in the conf file.  

see this link and look at the second post by tselliot [http://ubuntuforums.org/showthread.php?t=238380&highlight=cannot+change+resolution](http://ubuntuforums.org/showthread.php?t=238380&highlight=cannot+change+resolution)

---

### Post by dyous87 on 2006-10-04
> **Jordan Meeter said:**
> Yeah but what about me, who already has 1280x1024 listed in that file, yet cannot make their screen resolution bigger than 640x480? :p

Perhaps you're using the wrong drivers for you card. What type of graphics card do you have?

---

### Post by herrdoktor330 on 2006-10-05
> **sefs said:**
> Adding resoultions to conf file does not work for everyone.  There is a thread on here that suggest the use of the modline (i think its spelt like that) directive in the conf file.  

see this link and look at the second post by tselliot [http://ubuntuforums.org/showthread.php?t=238380&highlight=cannot+change+resolution](http://ubuntuforums.org/showthread.php?t=238380&highlight=cannot+change+resolution)

Well, darn. I thought I was helping. I'm still kind of new to this Linux thing. I assumed that the driver was installed if he was getting a res up to "1024x768".

---

### Post by sefs on 2006-10-06
I'm not taking away from what you said just adding on my 2 cents, so he has as much info as he can. :D 

> **herrdoktor330 said:**
> Well, darn. I thought I was helping. I'm still kind of new to this Linux thing. I assumed that the driver was installed if he was getting a res up to "1024x768".

---

