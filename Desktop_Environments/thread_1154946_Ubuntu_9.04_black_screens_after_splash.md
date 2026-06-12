---
title: "Ubuntu 9.04 black screens after splash"
date: 2009-05-10
forum: Desktop Environments
---

### Post by saywot on 2009-05-10
Based on my experiences with Ubuntu I recommended a pal to install the latest (9.04) for a happy and successful computing experience.

The installation went well, very well, it was quick and easy and everything went according to my experience of the distro.

Until.....

The next day this person connected to the internet and accepted all the updates on offer, then went and installed the restricted drivers for the PC.

The recommended drivers for the graphics were v.180 for an

nVIDIA GeForce 6100 nForce 405 chipset 

After a reboot there is no graphic output, it's a black screen, nada

So using the installation disc (running 'live') we were able to tell that there is no usable information in the /etc/X11/xorg.conf file - it says that it has a configured monitor and a configured screen (this isn't very helpful). 
OK now I told this person to press the <ESC> key in order to try and recover the machine. fixX didn't do anything to change the black screen inconvenience.
Using a shell and running "sudo apt-get remove nvidia-<TAB>" produces a 
E Couldn't find package nvidia-gix output

All of this has been over the 'phone

I would go and have a look at the machine myself, except it's 300 miles away !-

I'm going to need a few tips about how to proceed from this point

It worked until the restricted drivers were applied, I'm wondering if the package isn't installing all the kernel headers or something

What should I tell this person to do ?

---

### Post by saywot on 2009-05-11
running 'startx' in the <CTRL><ALT><F1> shell

produces a

> Fatal Server Error

how might one repair the windows-server from this shell

---

### Post by Ms Spock on 2009-05-11
:)

Thanks for all your assistance!

Spock

---

### Post by dedlycow on 2009-05-11
FREEZE
Acer aspire 5536/5236 Series.
AMD Athlon X2 64
Graphics ATI Radeon 4000 series
2 days old. Loaded Heron, upgraded to Ibex and then to Jaunty
restarted after what seemed like good install
The splash looked good then black screen with some pretty colours scattered accross the top of screen.
 I have tried to boot in recovery
 I have tried to boot from several live discs with no luck
 I cannot seem to get any OS to install
Any help or ideas appreciated
Dedly

---

### Post by saywot on 2009-05-11
> Graphics ATI Radeon 4000 series

Maybe the same problem
definitely a different GPU
If you can't set the BIOS to boot from an optical drive and either run 'live' or re-install then it's a different set of hardware problems

---

### Post by lhong1987 on 2009-05-26
Similar problem here.
Other ubuntu releases since 7.04 worked fine on this computer.
I have ATI Radeon XPRESS 200M.
9.04 installed fine, worked fine for few hours.

Grub and Splash screen comes out fine.
Then black screen with some weird colors comes up.
Soon my monitor (Hansol 17") fails to recognize the input anymore.
Cold boot, recovery mode, changing xorg.conf Device Identifier to vesa all failed.
XP dual boot works fine still.

---

