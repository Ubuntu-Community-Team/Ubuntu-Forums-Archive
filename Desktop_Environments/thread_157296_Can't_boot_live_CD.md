---
title: "Can't boot live CD"
date: 2006-04-08
forum: Desktop Environments
---

### Post by swawryk on 2006-04-08
Hello

I want to install linux on my notebook and set it up as a dual-boot system.  I am trying to evaluate ubuntu 5.10 because it has been highly recommended to me.   I have tried to start up with the live CD to check for any issues before installing it, but I can't get it working properly.

My platform is a Compaq Presario V2000 series (V2433AU) notebook with the following:
    * AMD Turion 64 processor
    * ATI Radeon Xpress 200M display adaptor

I have tried both the 32-bit and 64-bit PC versions.  Both fail during boot, but the 32-bit version gets a lot further into the boot process than the 64-bit version does so I'll focus on the 32-bit version here.

When the PC boots from the live CD everything goes well until it tries to start X windows (except that clock synchronization fails as expected without an internet connection when I do this offline).  When it attempts to start X windows (right after failing clock synchronization) it gets as far as blanking the background of virtual terminal vt7 then exits with error.

The file /var/log/Xorg.0.log shows hundreds of error reports at this point.  The following errors appear twice:
    drmOpenByBusid: drmOpenMinor returns -1023
    drmOpenDevice: node name is /dev/dri/card0
    drmOpenDevice: open result is -1, (Unknown error 999)
    drmOpenDevice: open result is -1, (Unknown error 999)
    drmOpenDevice: Open failed

Then "Unknown error 999" is replaced by "No such device" and repeats with "/dev/dri/card0" counting up to "/dev/dri/card254".  Eventually this all ends with the following reprts/errors:
    (II) RADEON(0): [drm] drmOpenFailed
    (EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.
    ...
    Fatal server error:
    Caught signal 4. Server aborting

The problem appears to be related to the ATI Radeon adaptor as far as I can tell.

One thing I forgot to write down was that I also tried it with a boot parameter suggestion I found in the start up help menus (driven by the function keys) that if there were [display/video?] problems to start up with "live <something>" where <something> was something like (from memory - this isn't exactly right) display=775.  This made no difference.

Has anyone seen anything like this?  Can anyone help me?

](*,) 

Thank you
Steve

---

### Post by slipk487 on 2006-04-09
ubuntu isnt really ATI friendly it took me a week to get my to work

---

### Post by swawryk on 2006-04-09
What did you do to get it to work?

:confused: 

Steve

---

### Post by slipk487 on 2006-04-09
i had it running on an intergrated card first and had to add a new kernel and driver inorder to get it to work

---

### Post by swawryk on 2006-04-09
Was that with an installation or with a live CD?

Steve

---

### Post by swawryk on 2006-04-21
[QUOTE=swawryk]Hello
When the PC boots from the live CD everything goes well until it tries to start X windows (except that clock synchronization fails as expected without an internet connection when I do this offline).  When it attempts to start X windows (right after failing clock synchronization) it gets as far as blanking the background of virtual terminal vt7 then exits with error.
[/QUOTE]

FWIW (if anyone's interested) to see if this problem has been dealt with on more recent releases I have just tried the live CD for 6.06 (Dapper Drake release 6).  It didn't have this problem for me.  So far so good ...

:D 
Steve

---

### Post by evilregis on 2006-04-21
Thanks for adding that... glad to hear it's working well for you so far...

---

