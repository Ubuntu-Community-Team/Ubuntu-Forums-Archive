---
title: "FAILED to initialize HAL problem"
date: 2005-04-01
forum: Desktop Environments
---

### Post by Soylent on 2005-04-01
Hi everybody

I'm totally new to this wonderful OS (linux as well as Ubuntu) but I've got everything up and running at this time. unfortunatly I'm still encountering an anoying bug. I got this from the Live cd and Hoary 5.04. After a fresh installation of the latter Xorg starts up pretty fast from the login to the desktop. But when I updated the packages via synaptic, the finilization of the desktop startup i.e. getting the icons in the two default toolbars and loading the wallpaper, is taking too long. And 50% of the time I get the ERROR: failed to initialize HAL. is there a found solotion for this problem. 

Thnk you all very much for reading this problem. 

Soylent

---

### Post by kagou on 2005-04-01
I had this probleme cause my dvd writer was bad (ricoh). That crash hal.
I had to put "hdc=noprobe hdc=cdrom" to kernel parameter in /boot/grub.menu.lst
hdc is my writer device
May be this help you

---

### Post by bigzak on 2005-04-01
[QUOTE=kagou]I had this probleme cause my dvd writer was bad (ricoh). That crash hal.
I had to put "hdc=noprobe hdc=cdrom" to kernel parameter in /boot/grub.menu.lst
[/QUOTE]

Just to second that, my DVD-ROM was causing the same problem (DVB drive, firmware from some newsgroup ;)) and this fixed it

---

### Post by dstrimble on 2005-04-14
I am having the same problem I have a Pioneer DVD Rom. I tried adding that to menu.lst and it did not work. Maybe I did not add it correctly, can someone post their menu.lst so I know exactly where to put the line?

Daniel

---

### Post by candrawardhana on 2005-07-29
i found that problem, and i will try to analize... 
the problem from my CDROM,

i can't mount my CDROM
and then, i can't eject it

i check  :
/mnt
my folder /cdrom lost!!!

well...
i try this :
sudo mkdir /mnt/cdrom
reboot

the problem finished


candrawardhana

---

### Post by mckooiker on 2007-12-20
I had a similar problem:
Laptop toshiba, Installation using WUBI. Fresh install/upgrade to 7.10
Upon starting up the computer I got the failed to initialize hal message.
After reading a bit I tried to turn of applications loaded on login one by one.
turning off the update notifier did the trick.....

---

### Post by Amarsingh0793 on 2008-03-14
Hi

If you have this problem, please follow these steps:
1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.

Thanks:)

---

### Post by Roasted on 2008-03-16
> **Amarsingh0793 said:**
> Hi

If you have this problem, please follow these steps:
1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.

Thanks:)

I just wanted to say I did this and it worked fine.

What causes these issues? I did a fresh install of Gutsy and installed a boatload of applications and sync'd all of my data back over to my home directory. Then magically I get the error. Why? What causes it?

Granted, it's fixed now, but I'm still curious what was up.

---

### Post by andoni on 2008-03-29
> **Amarsingh0793 said:**
> Hi

If you have this problem, please follow these steps:
1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.

Thanks:)
Oh thanks Amarsingh0793, I will try executing "sudo dpkg-reconfigure hal" becasue "S12dbus" is already in /etc/rc2.d.
Thanks ;).

---

### Post by mbogle on 2008-04-09
> **Amarsingh0793 said:**
> Hi

If you have this problem, please follow these steps:
1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.

Thanks:)

First off thanks for the suggestion.  Unfortunately I've confirmed the first 2 steps and have tried  sudo dpkg-reconfigure hal but to no avail.  The terminal sat there for several minutes before saying:

invoke rc-d : initscript hal, action "start" failed

In my case this problem only arose after installing the kernel 2.6.24-15-generic update.  When I boot into kernel 2.6.24-14-generic the message does not appear. 

Do you have any other suggestions I might try?

Thanks for the help,

Mike

---

### Post by Rob2008 on 2008-04-09
I am also having this problem but its not when i first install its when i do the first update :confused:

So i want to update but im scared to:(

---

### Post by j andersson on 2008-04-10
I'm in the same boat, failed to initialize HAL and no network with kernel .15
GeForce 6150SE nForce 430

---

### Post by captainneb on 2008-04-10
Same problem here.  Only after I try installing updates do I get the error "Failed to initialize HAL..."  I have since avoided installing updates but would like to know if there is a better fix.

---

### Post by j andersson on 2008-04-11
Still same problem with kernel .16:confused:

---

### Post by Amarsingh0793 on 2008-04-11
Hey everyone! Sorry for my late reply:)

As a temporary fix, every time you log in, press Alt + F2 and type "**_[U]sudo /etc/init.d/dbus restart_[/U]**" (without the quotes). Usually this error happens when you uncheck the System Communication DBus in Services. 

Hope this will do for now

---

### Post by tzulpc on 2008-07-12
> **Amarsingh0793 said:**
> Hey everyone! Sorry for my late reply:)

As a temporary fix, every time you log in, press Alt + F2 and type "**_[U]sudo /etc/init.d/dbus restart_[/U]**" (without the quotes). Usually this error happens when you uncheck the System Communication DBus in Services. 

Hope this will do for now

hi, i just had the same problem on my comp, but doing this fixed it, at least for now. However, as you say, I'll have to do this every time i boot my computer... Do you know how to fix this permanently? Thanks!

---

### Post by Amarsingh0793 on 2008-07-13
For a permanent fix, you could try what I said above:

Hi

If you have this problem, please follow these steps:
1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.

Thanks

---

