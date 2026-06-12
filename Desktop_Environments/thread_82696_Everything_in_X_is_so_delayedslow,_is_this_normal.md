---
title: "Everything in X is so delayed/slow, is this normal?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by hootpie on 2005-10-27
I have a system with the following specs:

AMD Athlon 950mhz T-Bird
640mb PC133 RAM
30GB HD
64mb Geforce 2 GTS Pro

People have always told me that Linux runs better on older computers than Windows does.  Ubuntu does not seem to run very fast at all.  In fact, IIRC, Ubuntu runs slower on this computer than Windows 98/2000/XP did.

By slow, I mean it takes roughly 5 seconds for Firefox to open after I select it, webpages in Firefox load slow, switching between tabs is really slow.  I thought it might just be Firefox, but this slowness extends to everything.

When I click menus, there is a 1-2 second delay before they open, when I try to open any utilities it takes a while too.

Overall, there seems like there's a delay on everything I do.  Is this normal for a system of my specs, or is something wrong?

---

### Post by user_stu on 2005-10-27
My experiences with various flavours of Linux matches yours. The GUI does feel and respond more slowly than XP. Debian seems to be among the most responsive of the distributions, whilst Red Hat and Suse seem slower. On the other hand Linux basically does not crash for me and can run indefinitely.

Re older hardware: I don't know why pple say it is suited to older hardware. As far as using Gnome or KDE desktops are concerned it is annoyingly slow as a desktop machine. Note that the use of alternative desktops and/or distributions (eg. Damn Small Linux???) may make a huge difference.

---

### Post by hootpie on 2005-10-27
[QUOTE=user_stu]My experiences with various flavours of Linux matches yours. The GUI does feel and respond more slowly than XP. Debian seems to be among the most responsive of the distributions, whilst Red Hat and Suse seem slower. On the other hand Linux basically does not crash for me and can run indefinitely.

Re older hardware: I don't know why pple say it is suited to older hardware. As far as using Gnome or KDE desktops are concerned it is annoyingly slow as a desktop machine. Note that the use of alternative desktops and/or distributions (eg. Damn Small Linux???) may make a huge difference.[/QUOTE]

As long as it's not a problem with my system and particular installation, I'm "happy."  It's unfortunate that this seems to be the theme with Linux as a desktop.  Is it the same way on faster machines?

---

### Post by user_stu on 2005-10-27
Im using a Toshiba notebook: P4 2.8 512Mb ram (shared for graphics). Things are much better than on P3 600, 512Mb ram, but still doesn't feel as snappy as XP when freshly booted. The one application I would say is borderline unusable for startup time, is Open Office 2. Takes 12 sec to open initially and then about 4 sec once cached. I guess if I were using it often I would just leave the launcher open (then it's as fast/faster than MS Word). In fact I have installed Abiword as an alternative to Open Office which loads in a couple of seconds or better.

However, I find that performance of apps on Linux don't deteriorate over time and/or with stressing the system by opening a ridiculous number of applications/windows etc. eg. while browsing internet.

---

### Post by Fillepe on 2005-10-27
In my experience with Linux I have found that applications tend to start slower than in Windows whilst things like Gnome menus tend to be faster than the start menu in Windows XP.

Plus any lack of speed in application startup is made up for by not having to spend time running virus scans etc although most would do this overnight...

My hardware is fairly similar to yours

Duron 1GHz
512Mb RAM
GeForce4 Ti4200 (running nvidia driver and RenderAccelleration=1)

I experience no noticible lag when I open menus though i suffer from much the same app startup times as you. Loading webpages in Firefox is no slower than Windows though it occasionally chokes when opening a link in a new tab.

And as for the "Linux is better for older hardware" bit, it can be if you want it to be. Ubuntu would perform worse on older hardware than Win98/2000 (maybe). If you had such hardware you would run a much more light weight system. Probably a much more customisable distro such as Gentoo.

Hope all this rambling helps.

---

### Post by Velvet Elvis on 2005-10-27
[QUOTE=hootpie]I have a system with the following specs:

AMD Athlon 950mhz T-Bird
640mb PC133 RAM
30GB HD
64mb Geforce 2 GTS Pro

People have always told me that Linux runs better on older computers than Windows does.  Ubuntu does not seem to run very fast at all.  In fact, IIRC, Ubuntu runs slower on this computer than Windows 98/2000/XP did.

By slow, I mean it takes roughly 5 seconds for Firefox to open after I select it, webpages in Firefox load slow, switching between tabs is really slow.  I thought it might just be Firefox, but this slowness extends to everything.

When I click menus, there is a 1-2 second delay before they open, when I try to open any utilities it takes a while too.

Overall, there seems like there's a delay on everything I do.  Is this normal for a system of my specs, or is something wrong?[/QUOTE]


If you're not already, make sure you are using the k7 kernal.

While out of the box linux may not be a speed demon, keep in mind that it's much much much more tweakable under the hood tan windows is.  Ubuntu probably isn't the best distro to use if you want to do a lot of tweaking though.  I'd personally recommend slackware or gentoo.

---

### Post by hootpie on 2005-10-27
[QUOTE=Velvet Elvis]If you're not already, make sure you are using the k7 kernal.

While out of the box linux may not be a speed demon, keep in mind that it's much much much more tweakable under the hood tan windows is.  Ubuntu probably isn't the best distro to use if you want to do a lot of tweaking though.  I'd personally recommend slackware or gentoo.[/QUOTE]

I used the K7 and that screwed things up for me.  It did not seem to speed up and all and it rendered my nvidia drivers useless (I updated the nvidia kernel modules and everything too).

What is RenderAccel, what does it do, would it help, and where do I find it?

---

### Post by Fillepe on 2005-10-27
It is an option that you can pass to your nvidia driver to make everything go faster. The effect is not dramatic but it may help. BEWARE There are many storys of it being buggy reducing X to a crawl and all kinds of other crazy things. Although if this happens it is easy to disable.  I personaly have had no problems with it over several machines and distros.

To enable it open the file /etc/X11/xorg.conf in gedit as root using

sudo gedit /etc/X11/xorg.conf

and find the section similar to this (my version)

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID	       "PCI:1:0:0"
EndSection

Bear in mind that yours will look silghtly different ie the Identifier will be different. Change that section to look like this

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID	       "PCI:1:0:0"
	Option	        "AGPMode"         "4"
# 	Option		"AGPFastWrite" 	  "True"
	Option	        "RenderAccel"     "1"
	Option		"NoLogo"
EndSection

The "AGPMode" ensures your card is running at AGP 4X, "RenderAccel" speeds stuff up and "NoLogo" gets rid of the anoying Nvidia logo in X startup.

If you want to turn "FastWrites" on I suggest googling the term (I cannot remember exactly what it does) and if you still feel the need remove the hash/pound mark from the front of that line.

Save the changes to this file and any other work you have open and restart X with Ctrl + Alt + BkSpce. Enjoy.

Hope it works out for you, let me know if you have problems.

---

