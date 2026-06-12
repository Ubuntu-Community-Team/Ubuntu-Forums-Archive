---
title: "resolution issue"
date: 2009-04-26
forum: General Help
---

### Post by terrordrone on 2009-04-26
on my office desktop (kubuntu 8.10)..  the resolution has been reset to 800x600

and xrandr gives :

```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0
   640x480        60.0
   400x300        60.0     56.0
   320x240        60.0

```

how do i get it back to 1024x768 or higher ?

thanks

---

### Post by tkelito on 2009-04-26
I'm sure Kubuntu is the same, what does your xorg.conf look like?

It will be in the /etc/X11/ directory.

You may have a failsafe backup already made in that folder that will be labeled xorg.conf.failsafe.

If you go into Terminal and run "sudo gedit /etc/X11/xorg.conf" you can then copy paste what your config looks like into here so we can see it.

Are you using any proprietary drivers?  You can check this by going into

System > Administration > Hardware Drivers

Your xorg.conf will also give us an idea of what driver you are running.  My guess is that your max 800x600 is set in the conf file and needs to be modified.

-tkelito

---

### Post by terrordrone on 2009-04-27
thanks for replying

That is my xorg.conf
```

....
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

afaik im not using any proprietary drivers as its an onboard gpu :|

there is no system > administration > hardware drivers on kubuntu 
(any other way to let you guys know ? from the cmd line)

i also notice that 945resolution app in synaptic is nowhere to be seen..

---

### Post by terrordrone on 2009-04-27
bump .. :sad:

is this the right sub forum ? do i have to post it elsewhere?

---

### Post by Sprut1 on 2009-04-27
Always backup xorg.conf before editing it. Here is a small clue on how to get things working (I'm not saying this will fix it):

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

```

I'd simply try this and restart X

---

### Post by terrordrone on 2009-04-27
i did as said.. 

its still the same

---

### Post by Sprut1 on 2009-04-27
> **terrordrone said:**
> i did as said.. 

its still the same

Did you try it with different resolutions? Just to check if anything at all happens? I'm really not an expert on this, but this is what I do to get my resolution correct :)

---

### Post by terrordrone on 2009-04-27
i can revert to other lower resolutions through the GUI itself.. but its 1024 or higher that i need :(

---

### Post by Sprut1 on 2009-04-27
> **terrordrone said:**
> i can revert to other lower resolutions through the GUI itself.. but its 1024 or higher that i need :(

Sounds too me like the exact problem I had. My monitor isn't recognised so I have to manually edit xorg.conf to get 1280x800 for my laptop, this is what I did. Are you sure you edited and saved xorg.conf correctly?

Sorry for not being able to help you out.

---

### Post by terrordrone on 2009-04-27
yea .. i did save it.. restarted the system to be completely sure..

checked the xorg.conf file after restart.. and it was saved .. but had no effect of changing the resolution though :( 

please dont be sorry.. wat matters is that youre trying to help :)

---

### Post by Sprut1 on 2009-04-27
> **terrordrone said:**
> yea .. i did save it.. restarted the system to be completely sure..

checked the xorg.conf file after restart.. and it was saved .. but had no effect of changing the resolution though :( 

please dont be sorry.. wat matters is that youre trying to help :)

Okay, then that obviously had no effect. Configuring xorg.conf manually is tricky business.

---

### Post by terrordrone on 2009-04-27
this is the video card on the machine :

```

01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev c1)

```

output is from lspci

---

