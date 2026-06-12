---
title: "Problem with Warcraft"
date: 2006-01-08
forum: Gaming &amp; Leisure
---

### Post by heart_reaver on 2006-01-08
Hi there, 

I want to run Warcraft Region of chaos on my old PC. Its configuration is 

P III, 866Mhz , 256 MB of Ram, Board is intel 810, no external graphic card attaced to 
it. When i had installed windows on it, it have worked on it and played smoothly.

I have installed warcraft on win partition and run it form cedega. Its runing but its runing slow. To check what problem is there i try to install planet penguin racer. It is having same problem. Frames are moving slow.

---

### Post by superm1 on 2006-01-08
You said that you aren't using external graphics chipset.  Check and see if you are using the intel drivers, or a regular old vesa driver.  If your using vesa, I would recommend a switch to the intel.  If your using the intel and having troubles still - i'd say invest in a low end ~$50 nvidia card.

---

### Post by Thirsteh on 2006-01-08
As superm1 said, check that you have the latest proper drivers, however, if games are still running with poor performance through Wine/Cedega while native games don't, try doing this command in a console then start your game:

sleep 30 renice 15 `pgrep wineserver`

You can try with other nice levels, but 15 should be "the safe one". In case you don't understand the above command, it doesn't do anything for 30 seconds after you've entered the command, allowing you to start your game and enter it before it changes the process nice (priority level) to a higher value than the default.

All best.

---

### Post by heart_reaver on 2006-01-08
[QUOTE=superm1]You said that you aren't using external graphics chipset.  Check and see if you are using the intel drivers, or a regular old vesa driver.  If your using vesa, I would recommend a switch to the intel.  If your using the intel and having troubles still - i'd say invest in a low end ~$50 nvidia card.[/QUOTE]


I am new to linux gaming how can i check that

---

### Post by superm1 on 2006-01-08
Well the easiest way is to look in your xorg.conf file. Its located in /etc/X11/xorg.conf.  You can open it up in gedit or your favorite editor.  Look for a section labeled device which describes your video card.  If your not too sure which is which, post the whole file here and we'll help.  

For example, here is my device section for my ATI card which uses the fglrx driver:  
```
Section "Device"         
     Identifier  "ATI Technologies, Inc. FireGL Mobility T2 (M10 NT)"         
     Driver      "fglrx"         
     Option      "PowerState" "1"         
     Option      "VideoOverlay" "on"         
     BusID       "PCI:1:0:0" 
EndSection
```

---

### Post by Thirsteh on 2006-01-08
If you have an Nvidia graphics adaptor and your Driver section says "nv" then you need to do the following (however judging from your original post I doubt you do :\):

sudo apt-get install nvidia-glx nvidia-settings

Edit your /etc/X11/xorg.conf and change "nv" to "nvidia".

Log out of Gnome, when you're at the login screen, hit CTRL+ALT+BACKSPACE. You can also reboot your machine.

---

### Post by heart_reaver on 2006-01-08
```

Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

```


This is what i found

---

### Post by Thirsteh on 2006-01-08
I'm afraid you should strongly contemplate investing in an Nvidia graphics adaptor, or rather, I heartily recommend that you do.

---

### Post by heart_reaver on 2006-01-08
then how it is working smooth in windows and choppy in ubuntu
the machine must not be the problem there is something in s/w i suppose

---

### Post by kaamos on 2006-01-08
Try running with the -opengl flag. This works in wine at least.

---

### Post by heart_reaver on 2006-01-08
[QUOTE=kaamos]Try running with the -opengl flag. This works in wine at least.[/QUOTE]
how to use this opengl flag with wine (im new to ubuntu:smile: )

---

### Post by kaamos on 2006-01-08
try this
```
cedega /path/to/warcraft/Warcraft\ III.exe -opengl
```

---

### Post by heart_reaver on 2006-01-08
-opengl is giving same responce as earlier.

I have installed ppracer (planet penguin racer). Then i run it with 

```

arjun@amnesty:~$ ppracer -opengl
PPRacer 0.3.1 --  http://racer.planetpenguin.de
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.
[B]
open /dev/sequencer: No such file or directory[/B]
arjun@amnesty:~$


```

I think as mentioned in bold line some thing is missing by me

---

