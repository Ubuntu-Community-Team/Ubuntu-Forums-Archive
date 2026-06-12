---
title: "Cant login"
date: 2005-10-13
forum: Desktop Environments
---

### Post by ch1n on 2005-10-13
I just wanna clear this first, Im not new to computers, but im new to linux.

Ive installed Ubuntu the latest in download section, and it works fine untill i try to login, after i login it just freezes. not even mouse is moving. thank god this comps works. :confused: 

I'd like a quick answer couse this is a school projekt, and i gotta get it to work with World Of Warcraft until Saturday.

// Johan in Sweden

---

### Post by karuptdata on 2005-10-13
Whats your hardware schematics?

---

### Post by ch1n on 2005-10-13
I have AMD 64 3000+, 1024 Dual Channel Twin Mos DDR, ATI Radeon x600 128mb, eeeeh MSI K8N Neo4, hmmm what more du u wanna know? :rolleyes:

---

### Post by ch1n on 2005-10-13
Would like to have some kind of answer, i need it to work and i dont want to spend more hours to just install it... :(

---

### Post by ch1n on 2005-10-13
Reinstalled it, but still the same problem... what shall i do?!:confused: :confused: :confused:

---

### Post by taurus on 2005-10-13
Maybe you want to run the memtest first to see if there is something wrong with your RAM!!!

---

### Post by claudiob on 2005-10-13
It happened the same on my desktop. Hoary was running smoothly; after the upgrade to Breezy I cannot login into my desktop.

When I confirm my login password in gdm the password area freezes (the screen is still active and I can select 'Language' and 'Session') and I cannot enter my desktop.

I am using an external ldap server for authentication but that is not the problem I think, since I can login via shell.

In /var/log/messages I see no entry after the password is sent.

I also tried to login in a fresh new home directory but result is the same.

---

### Post by weston on 2005-10-14
I have the exact same problem.  It seems to hang when trying to load GNOME.

I have a DELL 4600

2.8GHz HT P4
768 Ram (ram tested, passed)
NVidia 6800 LE Video Card

It is not an isolated problem... something is up here.

I just did a straight normal installation and it doesn't ever show the GNOME.
I can log in fine from terminal (CTRL-ALT-F1), but not thru the GUI.

Thanks guys!

---

### Post by claudiob on 2005-10-14
**Update:** I can succesfully login in my GNOME desktop if I kill the X server from a console as root and then as a normal user I issue the 'startx' command and can succesfully login (my desktop is in the window you reach with CTRL+ALT+F8).

If I do CTRL+ALT+F7 I can see the hanged (actually is active but you can't do anything) login window.

I still didn't manage how to solve this problem.

---

### Post by weston on 2005-10-14
so could this be a badly burnt CD?

NVidia problem?

what could cause this?

---

### Post by claudiob on 2005-10-14
[QUOTE=weston]so could this be a badly burnt CD?[/QUOTE]
I exclude this since I updated my Hoary changing the repositories 'hoary' to 'breezy' in Synaptic.

[QUOTE=weston]NVidia problem?[/QUOTE]
NVidia works good doing the trick above (startx) so it should not depend on this.
I suspect some gconf setting not related to the user settings in his homedir.

---

### Post by weston on 2005-10-14
what is strange is that I have the exact same problem, and I noticed some other post about the same thing.

I don't think its limited to us 3... it was just a perfectly normal install... We both have reinstalled to no avail.

Something basic is wrong here.   It seems to be with GNOME.  I may just have to use KDE, or would the edubuntu edition be any different?

---

### Post by brentoboy on 2005-10-14
I'm guessing you hear the drums. but dont see any startup action - brown background after login.  Mouse works, but nothing else.
--
I had the same problem.

restart, and use grub to boot to recovery mode - root console

#  nano /etc/X11/xorg.conf

find your video driver module: "ati", "nv" whatever
change it to "vesa"

save, and restart.
#  shutdown now -r

it should load.  the vesa driver has no optimizations, but it works in almost any environment.  Once you have it booting, you can look through the forums for help getting the "real" nvidia or ATI driver kicking - if you have a need for speed.

---

### Post by brentoboy on 2005-10-14
[QUOTE=weston] It seems to be with GNOME.  I may just have to use KDE, or would the edubuntu edition be any different?[/QUOTE]

I tried out edubuntu, and it looks like it is GNOME - it has a different icon scheme. Its actally plesant - but there are "cooler" custom icon schemes out there, so I didnt hold on to it long.

Didnt spend enough time really looking at it, so I dont know what advantages it really has over the regular ubuntu, but I think I answered the question at hand.

---

### Post by ch1n on 2005-10-14
Well im nooby i admit it.
When i login the screen is like it should, only that i dont see any icons and the mouse eventually freezes, and i have to do a hard reboot.
But during the installation i didnt got to do anything about the root pass so now i cant enter Root. :S and cant do anything about it from SU](*,) 
Please tell me what i can do and so on.
I want to know the commands and so on, couse i dont know linux at all... :(

I have to be able to use it in school 2morrow morning... but as things look now i might not make it... and get a F. :/

(edit: forgot to put in the essential ^^ )

---

### Post by tinwelint on 2005-10-14
I'm having exactly the same problem. It hangs when logging into gnome, only displaying the brown background and playing those drums over and over again.

I tried changing the driver in xorg.conf to "vesa". But it didn't help.
The problem remained exactly the same.

---

### Post by brentoboy on 2005-10-14
[QUOTE=ch1n]But during the installation i didnt got to do anything about the root pass so now i cant enter Root. :S and cant do anything about it from SU
[/QUOTE]

when your PC first starts up (right after memory count) you have 3 seconds to click escape to enter the grub menu.  If you make it in time, select recovery mode.  This will give you a text based root terminal (after it boots the basics).

if you dont make it in time, when it gets to the graphical login screen, click 
Ctrl Alt F1 (all at once)
This will give you a terminal (but xwindows is still runnin in a different world - you you will have to kill it)

it will ask you to login.  Give it whatever user you created when you installed, that is the "sudo" password.  (not root - just sudo)

once you login, you can 
$ sudo /etc/init.d/gdm stop
to kill the xwindows session trying to start (the one doomed to fail)

edit your config file to use the vesa driver (like I explained above)

restart your system after you save it.  it should work then. let me know how it goes.

---

### Post by weston on 2005-10-15
well brentoboy, you fixed my problem.

I seems it is the video drivers.  I imagine you could also run:

sudo dpkg-reconfigure xserver-xorg

and change it there rather than the text editor, but your way worked perfectly for me... now to download the new nvidia drivers.

Thanks!

---

### Post by tinwelint on 2005-10-15
Now I've tried several different video drivers but nothing seems to make any difference. It still hangs att the same place.
Could it be something else?

---

### Post by brentoboy on 2005-10-15
[QUOTE=tinwelint]Now I've tried several different video drivers but nothing seems to make any difference. It still hangs att the same place.
Could it be something else?[/QUOTE]

Find the section in xorg.conf that defines the driver for the video card. Mine looks like this:

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

What does yours say?
what have you tried?
What was in there first? nv? ati? ??

You want it to say something like this:

Section "Device"
	Identifier	"your card name"
	Driver		"vesa"
	BusID		"PCI:1:0:0"  # this might be different, but I doubt it
	Option		"UseFBDev"		"true"  # you dont really need this
EndSection

if that gives you trouble:
find this:

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

pulll out GLcore (just comment it out by putting a # in front of it) dri, and glx
Section "Module"
#	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
#	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

then save it, and restart your PC (or just X if you prefer)

---

### Post by tinwelint on 2005-10-15
Mine said:
```

Section "Device"
Identifier "ATI Radeon 9000 series" #something like that
Driver "ati" #not since i changed it to vesa
BusID "PCI:1:0:0"
EndSection

```

I have tried changing it both to vesa and to vga.

Just now I tried changing it to vesa as well as disabling the GLcore, dri, and glx modules. It didn't help.
Strange.

Update:
Actually. It worked. I just left it as it were for 15 minutes and eventually it was logged in as it should be. But it goes *really* slow. I'll try to find the "real" driver you mentioned earlier.

---

### Post by brentoboy on 2005-10-15
ATI's site is really a let down. After digging around, I found out that my graphics chipset (laptop ati mobility gx chip) wasnt supported by their linux driver - it appears that they only have linux drivers for "new" stuff.  Your chipset might be new enough.

There are a handful of howto posts for getting the ati drivers in place, I seriously recommend it, just make sure you save your semi-functional xorg.conf file becuase chances are you will need it again between now and the end of the vidio driver quest.

---

### Post by tinwelint on 2005-10-15
Thank you. Trying this tomorrow. It's 01.45 over here now.

---

### Post by claudiob on 2005-10-16
All my problems where related to the ldap authentication and gdm, here is my post for the solution in case you have the same problem:

[http://ubuntuforums.org/showpost.php?p=418327&postcount=3](http://ubuntuforums.org/showpost.php?p=418327&postcount=3)

---

### Post by esnyman on 2005-10-22
I have the same problem:
Intel P4 2.6
nVidia GF 6200

The mouse is active, but not the keyboard. Some of the other forums cover problems on ATI hardware but nothing on nVidia.

The harddisk seems to be active at unpredictable intervals. I have waited for 20 minutes or more, but with no results.

Anybody with a possible solution?

---

### Post by esnyman on 2005-10-22
The "vesa" driver entry in the xorg.conf worked for me. Why does breezy not install the nVidia drivers correctly? The screen was very slow so I updated the drivers to the correct nVidia drivers.

Busy downloading the latest drivers. I hope this will work correctly.

---

### Post by Iced on 2006-03-08
Hello,

New user here too, but not really to Linux.

I had a bad time trying to figure out what was wrong with mine as well.

Changing my /etc/X11/xorg.conf file to "vesa" from "nv" worked.

My symtoms were similar to others:
- could install fine (multiple times!)
- login screen was fine (until trying to log in)
- using ESC at boot time to boot to recovery mode worked fine.
- trying to change the 'session' on the login screen sometimes hung.
- after entering in login credentials, mouse was active but somewhat a blank screen.

Changing it to 'vesa' worked, and now I will try to get latest updates and latest nVidia drivers to see what happens.  I will update later.

--Iced

---

### Post by Iced on 2006-03-09
I'm good to go now.  In order to fix this problem, i had to do my steps above and then followed method 2 in the following link.
[Click Here](http://www.ubuntuforums.org/showthread.php?t=75074) for excellent step-by-step instructions on upgrading nVidia drivers.  My system has latest drivers now and is responding much faster.

---

