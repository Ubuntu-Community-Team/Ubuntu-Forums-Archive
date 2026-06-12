---
title: "OOo Base Wont work after installing Nvidia drivers"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Frans81 on 2006-09-16
The Problem that i am having is basically the OOo (Open Office.Org) Base program will stop responding when using any of the actions in the left panel for example clicking on the Tabels, Queries, Reports or Forms. This started to happen after installing the nvidia video drivers.
I left the computer alone for about 4 hours and the program was still not responding, so out came the old "Kill -9" to close it. ](*,) 
I have 2 machines and the exact same problem has happened to both.
I uninstalled OOo compleately and Re-installed; no difference.

the only clue is that when i run OOo from the console i get this. 

```
frans@frans-desktop:~$ ooffice -base
*** glibc detected *** free(): invalid pointer: 0xb619f678 ***
```

before the nvidia drivers were installed OOo Base worked fine, I installed the MySQL.com driver and connected to a MySQL server; No problems at all before the nvidia drivers were installed.

Is there anybody else out there with the same problem ?
can anybody else replicate this problem ?
is there anybody else out there that has solved this problem or knows the solution ?

Thank You !

---

### Post by Rhubarb on 2006-09-16
It does indeed seem that something about those nvidia drivers are indeed evil.
From a fresh install of Ubuntu 6.06, OOo Base works fine.
After downloading all the updates (OOo 2.02, kernel 2.6.15-26-386), OOo Base is still working fine.
After installing nvidia-glx, and changing the xorg.conf from 'nv' to 'nvidia', OOo Base is completely broken, can't create a new simple database, use any wizards.

The only workaround I've found is to use two versions of xorg.conf, one with 'nv' and the other with 'nvidia'.  So one for OOo Base, and one for games.

You could make a script to do this (say, "cp /etc/X11/xorg.conf.OOoBase /etc/X11/xorg.conf", and the other to copy the xorg.conf for games).  Scripts should go into /usr/bin/ and don't forget to do a "chmod +x" on 'em to enable you to execute them.  Then run the appropriate script with sudo or root privaleges, then press 'Ctrl + Alt + backspace' to restart X.

If ya need any more help on how to do all this, let me know.

I'm not sure who you should file a bug report with to get this fixed up, could be an OOo problem, glibc, or it could be nVidia.  Quite bizzare.

---

### Post by Rhubarb on 2006-09-16
Think I found the problem:
[http://ubuntuforums.org/showthread.php?t=136119&page=7]("http://ubuntuforums.org/showthread.php?t=136119&page=7")
All the good info can be found from post #62 onwards

"i went to /usr/lib32 and noticed two different libnvidia-tls.so.1.0.8178, one in the same directory and the other in "nvidia" and a simlink ( libnvidia-tls.so.1) pointing to the first one. i made it point to the second one and it WORKED !"

So nVidia had messed up a bit here, to fix it all up:
```
sudo mv /usr/lib32/libnvidia-tls.so.1.0.8178 /usr/lib32/backup_of_libnvidia-tls.so.1.0.8178
sudo cp /usr/lib32/nvidia/libnvidia-tls.so.1.0.8178 /usr/lib32/libnvidia-tls.so.1.0.8178
sudo ldconfig
```

"The faulty libnvidia-tls.so.1.0.8178 is 2108 bytes,the working one is 2156 bytes"

I haven't tried this out yet, will get 'round to doing this tonight / tomorrow.  A few other posts around are suggesting that it could be the java virtual machine, in which case you'd have to install sun's java.  Good news (I'm guessing anyway) is that Sun are in the process of open sourcing their java, so hopefully the java aspect in future won't create any dramas with OOo, or Azeurus (I can never spell that properly) for that matter.

Please post here if you get it working, I'm curious to know.

---

### Post by Rhubarb on 2006-09-16
As the above info is from March 2006, it could be a little old.
Perhaps the latest nvidia drivers might fix it up for you.

tseliot has done some good work with regards to nvidia drivers, so you can get the latest from nvidia's website, or you can do it tseliot's way (easier):
[http://www.ubuntuforums.org/showthread.php?p=1494608#post1494608](http://www.ubuntuforums.org/showthread.php?p=1494608#post1494608)

---

### Post by Frans81 on 2006-09-16
I Got it working !!! :grin:
i changed the /etc/X11/xorg.conf from this
```
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"[COLOR="Red"]nvidia[/COLOR]"
	BusID		"PCI:3:0:0"
EndSection
```

To this
```
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"[COLOR="Red"]nv[/COLOR]"
	BusID		"PCI:3:0:0"
EndSection
```

However the video performance is shithouse.
Well, its better than nothing !!
i will just have to change the xorg.conf when i want to use the OOo base for now.

Thank you Rhubarb.

Does anybody know what exactly the problem is with the nvidia drivers and this problem ?, or what to do about it ?

---

### Post by Rhubarb on 2006-09-23
Seems like this is all working now, without having to do any annoying /etc/X11/xorg.config editing / mucking around.

I currently have the latest updates (September 23rd, 2006), running:
kernel 2.6.15-27-686
OOo 2.02
nVidia 1.0.8762+2.6.15.11-5 NVIDIA binary XFree86 4.x/X.Org driver

OOo Base just works like it used to now, with nVidia openGL acceleration.

Thankyou devs for fixing this up :D

---

### Post by wvernon on 2006-09-26
I can't open base - it just freezes whenever I try to.

I don't actually have the directories listed in the fix described here. I have lib, not lib32, and the versions of libnvidia-tls.so. I assume that this is due to the architecture of my computer rather than anything else.

I have a usr/lib/tls file that contains copies of the lib files discussed, but copying the '2156' byte version as discussed doesn't work.

Also, I've just done a fresh install on a box without an nvidia card, and it doesn't work on that either!

Wayne

---

### Post by Frans81 on 2006-09-27
The first fix didn't work for me either, i have no lib32 directory. the way i got it working was editing the /etc/X11/xorg.conf to change the nvidia entry to nv as stated above.

does the program start at all ie. does it draw the window and content ?

what sort of hardware are you running ?
if you have booting from the live cd, will it work from that ?
have you tried installing the version you have on another computer ?

---

