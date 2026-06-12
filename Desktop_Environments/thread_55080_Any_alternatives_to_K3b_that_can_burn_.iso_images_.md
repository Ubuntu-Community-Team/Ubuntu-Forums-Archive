---
title: "Any alternatives to K3b that can burn .iso images onto discs?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-08-07
I am having errors with K3b.  In fact, out of the 10 times I tried it, it only worked twice.  

Are there any KDE alternatives that I can burn images onto a disc, so that they are bootable?

---

### Post by c-m on 2005-08-07
[QUOTE=arcanistherogue]I am having errors with K3b.  In fact, out of the 10 times I tried it, it only worked twice.  

Are there any KDE alternatives that I can burn images onto a disc, so that they are bootable?[/QUOTE]
 what about nero for linux?

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 do have cdrdao installed for K3B ...

---

### Post by drizek on 2005-08-07
[QUOTE=c-m]what about nero for linux?[/QUOTE]
 k3b is by far the best. try to figure out what is wrong with it.

---

### Post by arcanistherogue on 2005-08-07
Ok, I'll post the error, and yes, I apt-get'd cdrdao.

first, it says: 

Size Calculated 91093 blocks
Using cdrecord 2.1a38 - Copyright (C) 1995-2004 Joerg Schilling
Starting tao writing at 4x speed...
Starting in 2 seconds
Starting in 1 second
(X)Mkisofs returned an unknown error (code 255).
(X)Unknown Error 255
(X)Please send me an email with the last output.

so I hit "show debugging output", and here is what it says:


[SIZE=1]> mkisofs
-----------------------
91093
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Size of boot image is 363660 sectors -> /usr/bin/mkisofs: Error - boot image '/tmp/kde-john/k3bMEZP4a.tmp' has not an allowable size.

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-john/k3bsYIhwa.tmp -rational-rock -hide-list /tmp/kde-john/k3baoUKNb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-john/k3bpKsKSa.tmp -eltorito-boot boot/slax-5.0.6.iso -eltorito-catalog boot/boot.cataloge /home/john/.kde/share/apps/k3b/temp/dummydir0/ 
[/SIZE]

---

### Post by gingermark on 2005-08-07
Gnomebaker is obviously a gnome application but works well enough in KDE and burns iso's a treat.

---

### Post by geearf on 2005-08-07
I have problems with k3b also, it always tells me to put a CD/DVD-/+R in there, even if tells me that the one in is empty ... I just need to force it, but that is not nice :(

---

### Post by lakcaj on 2005-08-07
Edit - didn't notice you wanted a KDE app.

---

### Post by drizek on 2005-08-07
[QUOTE=arcanistherogue]Ok, I'll post the error, and yes, I apt-get'd cdrdao.

first, it says: 

Size Calculated 91093 blocks
Using cdrecord 2.1a38 - Copyright (C) 1995-2004 Joerg Schilling
Starting tao writing at 4x speed...
Starting in 2 seconds
Starting in 1 second
(X)Mkisofs returned an unknown error (code 255).
(X)Unknown Error 255
(X)Please send me an email with the last output.

so I hit "show debugging output", and here is what it says:


[SIZE=1][/SIZE][/QUOTE]
 there is a new k3b .12 you might want to try upgrading to that.

---

### Post by woedend on 2005-08-07
not KDE..but X.  Graveman.  The only app to perfectly burn every ISO image.  its super small, in the repositories.  Just click duplicate CD, and from source choose ISO image and burn!

---

### Post by c0rderr0y on 2005-08-08
Might want to check if dma is enabled that is a common problem with burning errors in linux

---

### Post by mejajephky on 2005-08-12
Graveman is the answer! 
After spending hours trying to decide what the issue was and going through quite a large stack of blanks, I finally gave up on K3B. 
Sure enough, graveman was an easy install and burned the ISO's on the first shot, every time.
Thank you! Thank you! for you helpful advice.

---

### Post by cowlip on 2005-08-12
[QUOTE=mejajephky]Graveman is the answer! 
After spending hours trying to decide what the issue was and going through quite a large stack of blanks, I finally gave up on K3B. 
Sure enough, graveman was an easy install and burned the ISO's on the first shot, every time.
Thank you! Thank you! for you helpful advice.[/QUOTE]
 HI, be sure to install gtk2-engines-gtk-qt if you want it to look like it's a kde app

---

### Post by Gezzer on 2005-08-12
installed graveman and tried it out
it works perfect, easy to use & set up
just what a burning app should be like

K3B has just been uninstalled ...

---

### Post by wrtrdood on 2005-08-12
Plenty of options and many already noted.  Did you know that burning an ISO file is elementary from the command line?

cdrecord -v dev=0,0,0 speed=48 mydisk.iso

You can get the device value using:

cdrecord -scanbus


The speed is the max your device can use.  The -v prints the progress.  mydisk.iso is the file you want to burn to the CD.


Just a thought...

---

