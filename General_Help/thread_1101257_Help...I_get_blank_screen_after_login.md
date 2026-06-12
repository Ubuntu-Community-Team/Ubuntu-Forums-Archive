---
title: "Help...I get blank screen after login"
date: 2009-03-20
forum: General Help
---

### Post by cdoebbler on 2009-03-20
When I login I get a blank screen. 

I recently used the synaptic package manager to remove a virtual gnome package that I was not using but now my system seems to crash. It starts to boot, allows me to login (including to terminal mode), but after I enter my login and password the system seems to hang on a blank screen. That is I get no desktop view. I can boot from a disk but then my files are locked. I apparently removed as necessary file. Is there any way to restore this?

---

### Post by dcstar on 2009-03-20
> **cdoebbler said:**
> When I login I get a blank screen. 

I recently used the synaptic package manager to remove a virtual gnome package that I was not using but now my system seems to crash. It starts to boot, allows me to login (including to terminal mode), but after I enter my login and password the system seems to hang on a blank screen. That is I get no desktop view. I can boot from a disk but then my files are locked. I apparently removed as necessary file. Is there any way to restore this?

CTRL-ALT-F1 then log in
```
sudo apt-get install package-name
```

---

### Post by cdoebbler on 2009-03-22
I don't know which programme/package was removed as several related to virtual machine were removed. Moreover I can't get an internet connection if I cannot boot.

Is there no way to merely re-install ubuntu so that the needed gnome packages are recreated? From the forums it appears that this is not the case, which means I have lost so much work...more than six months of work.

---

### Post by cdoebbler on 2009-03-22
1. I can login and enter password, but then system seem to hang with blank screen.

2. I can use terminal with Ctl-Alt-F1.

3. I have no internet connection.

4. When I run dpkg -l | grep linux-image this is what I get:

ii  linux-image-2.6.24-16-generic        2.6.24-16.30 
 Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-21-generic        2.6.24-21.43 
 Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-22-generic        2.6.24-22.45 
 Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-23-generic        2.6.24-23.48 
 Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.24-23-virtual        2.6.24-23.48 
 Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                  2.6.24.23.25
 Generic Linux kernel image

5. when I run other sudo apt-get commands such as update, upgrade, install...I hit problems because I don't have internet connection on this old Viao PCG-TR3A. 
 
6. I do have earlier ubuntu 8.04 disk that has Ubuntu with GNOME and can add new partition and Ubuntu system, but still can't seem to access old locked files.

Any help or advice appreciated. Thank you.

Curtis

---

### Post by LiamWilson on 2009-03-22
Is it a white screen or a black screen?

---

### Post by cdoebbler on 2009-03-22
The screen is orangish...as if Ubuntu is launching, but it just stays blank and no desktop comes up. I can go to terminal with Ctl+Alt+F1.

---

### Post by prostar on 2009-03-22
I'm in the same boat right now. I can log into my XFCE session, but not my wife's Gnome session.

Race you to the answer!

---

### Post by prostar on 2009-03-22
Beat ya. If you don't have another user you can log into a terminal (Ctrl+Alt+F1).  Then remove the all the files under .gconf .gconfd .gnome2. You will lose all your setup, but it's faster than figuring out which one is the problem. You could also delete files/folders under those directories one at a time untill you find it, but I don't have patience for that.

---

### Post by cdoebbler on 2009-03-23
Thank you prostar, but how do I do this in terminal mode. I assume rm [filename] but when I go to .gconf there are two folders (desktop and another) and I cannot erase/remove them.

If I do remove them...will they be rebuilt? Don't I need them to run Ubuntu?

---

### Post by cdoebbler on 2009-03-23
I try to erase the files in .gconf...etc, but cannot easre them with rm and have no access to other command (eg, -r)

---

### Post by cdoebbler on 2009-03-23
tried:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and creating new user, without success...

but still no help.

---

### Post by byte.me on 2009-04-13
Nearly in the same boat here.  Just installed Debian 4 r03 a few days ago on an IBM A20p.  All was roses and happy tunes...after the initial aches and pains of hacking together a working xorg.conf configuration and getting my WPC54gs to connect to my AP...

Alas, I ran apt-get update network-manager-gnome and woe is me...

It fired up and at least 8 packages were removed and some 285 were d/l'd and installed.  

When I logged back in after reboot I have encountered a black screen with my cursor.  I have ctrl-alt-f5'd out to a console and run get-apt update.  Several times.  I have also tried a few suggestions found here in the ubuntu forums (you guys seem to be on the ball!) yet am unable to resolve this. :mad:

I'm a tinkerer by nature so I'd rather resolve the issue rather than wiping and starting over...as that path will eventually lead me right back to where I am now.  So I seek knowledge!

Desperately seeking a resolution!  Thanks!

Byte

---

