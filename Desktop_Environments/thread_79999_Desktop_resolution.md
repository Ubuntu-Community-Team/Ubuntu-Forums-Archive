---
title: "Desktop resolution"
date: 2005-10-21
forum: Desktop Environments
---

### Post by bete on 2005-10-21
So, i installed Ubuntu and everything seems fine and dandy - other than my screen resolution being 800x600, and i cant change it to something higher...

The graphic card supports a higher resolution. Any ideas?

---

### Post by migueljacq on 2005-10-21
Go to your terminal and type

sudo dpkg-reconfigure xserver-xorg

and configure your resolution settings from there (carefully)

---

### Post by bete on 2005-10-21
That was a bit to tricky for me, it asked me several questions like wich graphics card i have, wich type, and busID?

> Users of PowerPC machines, and users of any computer with multiple video devices, should specify
the BusID of the video card in an accepted bus-specific format.


---

### Post by bete on 2005-10-24
Bump!
Is there not a more simple way?

---

### Post by chhimed.w on 2005-10-24
[QUOTE=bete]Bump!
Is there not a more simple way?[/QUOTE]

Indeed there is!

From your desktop: 

Click on System/Preferences/Screen Resolution and simply set your reolution to the highest that your monitor can handle. :cool:

---

### Post by bete on 2005-10-24
[QUOTE=chhimed.w]Indeed there is!

From your desktop: 

Click on System/Preferences/Screen Resolution and simply set your reolution to the highest that your monitor can handle. :cool:[/QUOTE]

ok, not thaaat simple :P Because that doesnt work.. it only shows 640x480 and 800x600, wich i am currently using. But i want atleast 1024x800 or 1280x1024 wich i KNOW this screen handles because i use it on windows :).

I am fearing that my graphics drivers are not installed.. Is there a way to check what graphics card i have without opening my computer? 

And if someone could point me to a guide to install my graphics card that would be nice :).

---

### Post by cbudden on 2005-10-24
Do this sudo dpkg-reconfigure xserver-xorg take all the default options but make sure you check the resolutions you want at the end.

---

### Post by heimo on 2005-10-24
You could run this on terminal, to get a hint which graphics card you have:
```
lspci | grep VGA
```

My suggestion would be to shut down X and run reconfiguration again (with autoprobing). To do that, you need to run sudo /etc/init.d/gdm stop (this will put you into command line, no graphical user interface), login, make a copy of your current xorg.conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup), reconfigure using the dpkg-reconfigure-thingy, use autodetection and restart gdm using sudo /etc/init.d/gdm start, if that doesn't work, you can copy back the backup conf using sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by bete on 2005-10-24
[QUOTE=cbudden]Do this sudo dpkg-reconfigure xserver-xorg take all the default options but make sure you check the resolutions you want at the end.[/QUOTE]

Did all that just now, completed it successfully, but nothing happend after that.. so i tried to reboot.. But still the max resolution is 800x600... I dont think the graphics card is installed because windows resize slowly and stuff :P. 
So, how do i install my graphics card?


VGA compatible controller: ATI Technologies Inc 264VT [Mach64 VT] (rev 40)

---

### Post by migueljacq on 2005-10-24
actually one of my ubuntu boxes has a Radeon ATI and same problem - frankly it's a test machine so I couldn't care less - but yeah, interesting. I did run the xorg reconfigure and it didn't help either. my other machine is nvidia and worked like a treat. maybe an ATI thing?

---

### Post by bete on 2005-10-24
[QUOTE=migueljacq]actually one of my ubuntu boxes has a Radeon ATI and same problem - frankly it's a test machine so I couldn't care less - but yeah, interesting. I did run the xorg reconfigure and it didn't help either. my other machine is nvidia and worked like a treat. maybe an ATI thing?[/QUOTE]

Actually, when i installed ubuntu about a year ago on my main computer, i couldnt install the driver either, so i was stuck at 800x600 back then aswell..

The graphics card i have on my main computer is (duuh) ATI Radeon x800 pro.

So this seems to be an ATI thing.. 
:mad:

---

### Post by taavi on 2005-10-24
One way is to backup your xorg.conf file (/etc/X11/xorg.conf) and edit needed lines by hand. If finished editing restart Xorg (not Ubuntu, but Ctrl-Alt-Backspace restart;). It's somewhere in the Screens section, but I can't specify any further, because I don't have running Linux at hand. 

This isn't awfuly complicated, but you have to dig in.

---

### Post by bete on 2005-10-24
[QUOTE=taavi]One way is to backup your xorg.conf file (/etc/X11/xorg.conf) and edit needed lines by hand. If finished editing restart Xorg (not Ubuntu, but Ctrl-Alt-Backspace restart;). It's somewhere in the Screens section, but I can't specify any further, because I don't have running Linux at hand. 

This isn't awfuly complicated, but you have to dig in.[/QUOTE]

Ok i did that, and now i have the desktop resolution up to 832x624, even if i chose 1024x768..

I think my graphics card is not installed correctly..
Does anyone know how to install an ATI card?
ATI Technologies Inc 264VT [Mach64 VT] (rev 40)

---

### Post by migueljacq on 2005-10-25
Found this thread: might help?

[http://www.ubuntuforums.org/showthread.php?t=65276](http://www.ubuntuforums.org/showthread.php?t=65276)

---

