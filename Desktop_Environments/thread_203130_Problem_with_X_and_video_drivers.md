---
title: "Problem with X and video drivers"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Dark Shikari on 2006-06-24
I installed Ubuntu on one of my boxes to replace an aging Windows installation.  Everything worked great, as expected, but I noticed a problem: OpenGL applications weren't working, the full set of resolutions weren't supported, and basically all the usual signs of a lack of recent video drivers.

I follow the standard instructions to install the nVidia drivers, and it all worked... and then upon reboot X failed to load.

It appears that Ubuntu had detected my GeForce 3 TI200... as a Radeon 7000?!!!!  and thus the drivers obviously broke things.

1.  What do I do to Xorg.conf to make Ubuntu recognize the fact that this sure as heck isn't a Radeon?

2.  Is there anything I have to do after that to get it booting to X again?

---

### Post by lamego on 2006-06-24
Are you sure you have installed the correct driver ?
I am not very familiar with nvidia drivers but I know there are 2 drivers, one for legacy (older) cards and another for the latest. If you have installed the wrong dirver that would explain the problem...

---

### Post by krondar on 2006-06-24
[QUOTE=Dark Shikari]
1.  What do I do to Xorg.conf to make Ubuntu recognize the fact that this sure as heck isn't a Radeon?

2.  Is there anything I have to do after that to get it booting to X again?
[/QUOTE]

Ad 1. In simple words find Section "Device" in the end of the file and change Driver to "nvidia" :) If you installed the package it should work.

Ad 2. It should go ok without any changes :) My Debian did, so imo Ubuntu will act the same ;) I don't think that he changes runlevel apps when it does some problems. Default runlevel is 2 (you can check in /etc/inittab) and then look into /etc/rc2.d for gdm file :) (S13gdm)
Good luck ;)

And one more thing - for OpenGL you will need to install nvidia-glx package. The fastest way will be:
sudo apt-get install nvidia-glx
:)

---

### Post by Dark Shikari on 2006-06-24
[QUOTE=lamego]Are you sure you have installed the correct driver ?
I am not very familiar with nvidia drivers but I know there are 2 drivers, one for legacy (older) cards and another for the latest. If you have installed the wrong dirver that would explain the problem...[/QUOTE]
I used the correct one, yes.

[QUOTE=krondar]Ad 1. In simple words find Section "Device" in the end of the file and change Driver to "nvidia" :) If you installed the package it should work.
[/quote]
OK, I'll try that.
[QUOTE=krondar]
Ad 2. It should go ok without any changes :) My Debian did, so imo Ubuntu will act the same ;) I don't think that he changes runlevel apps when it does some problems. Default runlevel is 2 (you can check in /etc/inittab) and then look into /etc/rc2.d for gdm file :) (S13gdm)
Good luck ;)

And one more thing - for OpenGL you will need to install nvidia-glx package. The fastest way will be:
sudo apt-get install nvidia-glx
:)[/QUOTE]
Already done... thats what broke it in the first place.

---

### Post by Dark Shikari on 2006-06-24
Eh, krondar... it already says nvidia under Driver.  But X won't start.

---

### Post by krondar on 2006-06-24
What error the X Server is giving?

---

### Post by Dark Shikari on 2006-06-24
[QUOTE=krondar]What error the X Server is giving?[/QUOTE]
WW (warning): No matching device for BusID PCI:1:0:0.
EE (error): No device detected.

---

### Post by Dark Shikari on 2006-06-24
I got it to work by replacing the line BusID PCI:0:5:0 (I think) with the requested PCI:1:0:0.  However, among other things, it now won't accept any refresh rate other than 85hz, which is very bad because the monitor for this machine is crap and wiggles at any refresh rate above 60hz.

However, OpenGL now works.

---

### Post by Dark Shikari on 2006-06-24
Another problem I've had is that I need the package "x-window-system-dev" and other Ubuntu users have reported being able to download it, but apt-get says that it doesn't exist.  Is there a special repository I need to add to download this?

---

### Post by Dark Shikari on 2006-06-25
bump?  I need the refresh rate issue solved... it hurts my eyes to look at the jiggling screen.

---

### Post by tseliot on 2006-06-25
[QUOTE=Dark Shikari]I got it to work by replacing the line BusID PCI:0:5:0 (I think) with the requested PCI:1:0:0.  However, among other things, it now won't accept any refresh rate other than 85hz, which is very bad because the monitor for this machine is crap and wiggles at any refresh rate above 60hz.

However, OpenGL now works.[/QUOTE]
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")
If that doesn't work try point 10

---

### Post by tseliot on 2006-06-25
[QUOTE=Dark Shikari]Another problem I've had is that I need the package "x-window-system-dev" and other Ubuntu users have reported being able to download it, but apt-get says that it doesn't exist.  Is there a special repository I need to add to download this?[/QUOTE]
```
sudo apt-get install xserver-xorg-dev
```

---

### Post by Dark Shikari on 2006-06-25
[QUOTE=tseliot]Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")
If that doesn't work try point 10[/QUOTE]
Thanks a lot: point 5 didn't work, but point 10 most definitely did.

And thanks for the reference to the correct Ubuntu package 8)

---

### Post by Dark Shikari on 2006-06-25
Since I already have a thread, I might as well ask my further questions here.

I installed the CVS version of Cedega using the guide and script [here]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp;amp;amp;amp;back=HOWTO+INDEX+Wine").

I set it up, and it should work properly.  I did have to redirect the fonts folder (since none existed in the Cedega directory) to the /usr/share/fonts/truetype folder.  I then went to start Starcraft (which works fine, albeit slowly, under the original Wine, and Battle.net is buggy).  I quickly get:

wine: Unhandled exception, starting debugger...
err:seh:EXC_DefaultHandling Unhandled exception code c0000005 flags 0 addr 0xb7ce5855

Googling c0000005 informs me that this is a buffer overrun error.  Is this a common problem, or something weird that has no obvious solution?  I get this error no matter what program I attempt to launch in Cedega, so it isn't a game-related issue.

---

### Post by Dark Shikari on 2006-06-25
And another problem: I went to connect to my other computer, which is in Windows and has File Sharing enabled, and all went smoothly until I double clicked on the computer in the File Browser... I got:
> 
The filename "JASON1" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

?????

---

### Post by Dark Shikari on 2006-06-25
Bump?

---

### Post by Dark Shikari on 2006-06-25
bump?

---

