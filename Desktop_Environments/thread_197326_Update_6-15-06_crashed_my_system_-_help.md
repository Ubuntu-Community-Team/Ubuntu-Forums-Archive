---
title: "Update 6-15-06 crashed my system - help"
date: 2006-06-15
forum: Desktop Environments
---

### Post by headcronie on 2006-06-15
Think the linux kernel update did me in.  But really I have no idea.  The auto update feature of Ubuntu said there were 8 updates to install.  I said ok, install them.  Prompted me for a reboot and I got a kernel panic - system halted.  

I'm less than a week old in Linux.  I hardly know what I'm doing.

Here's what I've got for the booting error:

Booting 'Ubuntu, kernel 2.6.15.-25-386'

root  (hd0,0)
  Filesystem type is ext2fs, partition type 0x83
kernel  /vmlinuz-2.6.15-25-386 root=dev/hdb3 ro quiet splash
      [Linux-initrd @ 0xfa17000, 0x1c9000 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[    35.554023] RAMDISK: ran out of compressed data
[    35.554104] invalid compressed format (err=1)
[    35.555626] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[    35.555686]

That's where I'm at.. heeeelp.   :cry: 

Without rebooting into Live CD mode, these are my basics of my computer:

IBM Aptiva Model 2170-175
AMD K6-2 550mhz processor
256mb SD PC100 RAM
4gb HD
Diamond Stealth III 32mb PCI graphics card

16mb /boot partition
518mb /linux swap partition
3.x / partion

I can find out more if needbe by doing a Live CD boot.

I do need that /boot partition at the beginning of my hdd, as my bios is too stinking old to boot from anywhere else on the hdd, without giving me a grub boot error 18.

Hope I've provided enough to get started... any and all help is appreciated!
Thanks!

---

### Post by popkid on 2006-06-15
Hi, it could well be the kernel that has caused the problem,

when you boot, you should get a message, grub loading press f1 or something for options.... this only pops up for a couple of seconds so be quick!

you should then be able to scroll down and select the older kernel version that was working before (v23 instead of v25), should be about 4th in list below the safe options for the new kernel

if you can get that far then uninstall the newer kernel that is causing you problems, you should be able to do this in synaptic and it should remove the grub boot entry

hope this helps

pK

---

### Post by headcronie on 2006-06-15
Found it, tried it, got a screen and a half of errors... can't scroll back to see what happened...

Tried recovery mode.
Appears to be saying root device hdb3 is not a correct boot option... but again, I'm very new at this... I don't really understand what I'm reading.

---

### Post by headcronie on 2006-06-15
Ok, selected wrong recovery mode, I seem to be making some progress.. I'm at the console prompt in the 23 kernel recovery mode... what do I do?

---

### Post by Jasper Houtman on 2006-06-15
Wrong recovery mode again, select the one above the one you just selected to get the v23 command line.

this should load up ubuntu with your previous kernel.

log in and open the systems menu (top menubar)
open the administration menu and klick on the synaptic package manager.

klick on the search button, type "kernel 25" and klick on search.

look for linux-image-2.6.15-25-* (*= either 386, 686 or K7, should be the only one marked green).

Right click on the green square and select mark for complete removal.

This should complete remove the v25 kernel from your system and grub.

Note: if this failes I strongly recommend a clean install!!!

Good luck!

---

### Post by headcronie on 2006-06-15
Sorry to keep rambling by myself, but a bit of fooling around... typed exit, brought up the gnome desktop, got into the package installer, removed todays kernel update, and I'm rebooting now.  It looks good so far!  *fingers crossed*

I'm in!

Thanks for the pointers on how to get this process started.  :)

---

### Post by popkid on 2006-06-15
[QUOTE=headcronie]Ok, selected wrong recovery mode, I seem to be making some progress.. I'm at the console prompt in the 23 kernel recovery mode... what do I do?[/QUOTE]

rather than selecting recovery mode, you should be able to just boot the regular 23 kernel, may make life easier....

from where you are though, you should be able to do the following...

sudo nano /boot/grub/menu.lst

edit that by commenting the v25 kernel lines (put a # in front of all lines for each v25 boot option)

then when you boot you should automatically come back to v23

hope that helps...

pK

---

### Post by popkid on 2006-06-15
[QUOTE=headcronie]Sorry to keep rambling by myself, but a bit of fooling around... typed exit, brought up the gnome desktop, got into the package installer, removed todays kernel update, and I'm rebooting now.  It looks good so far!  *fingers crossed*

I'm in!

Thanks for the pointers on how to get this process started.  :)[/QUOTE]

no problem, hope it works out for you

pK

---

### Post by Fatjoint on 2006-06-15
[QUOTE=headcronie]Sorry to keep rambling by myself, but a bit of fooling around... typed exit, brought up the gnome desktop, got into the package installer, removed todays kernel update, and I'm rebooting now.  It looks good so far!  *fingers crossed*

I'm in!

Thanks for the pointers on how to get this process started.  :)[/QUOTE]

Glad you made it out OK!  

However - something you should think about is how you got yourself in this jam in the first place.

I had this problem not long ago myself as I'm learning as well.  It seems that Linux stores the Linux-Image Kernerls in the /boot partition.  These files seem to be a few megabytes a piece and over time can add up to be quite a bit.

My mistake was that I partitioned my /boot directory as something ridiculously small, like 10-15 MB and I'm suspecting you probably did the same or something simular.

I reinstalled, but what are your options?  Since you're up and working again, it definately would be the time to start that portion of the conversation and I'm interested in finding out what could be done.

---

### Post by headcronie on 2006-06-17
Here's my problem.  My bios has to have the kernel in the first few MB of the hd or I get the dreaded Grub Error 18.  So, question is this... how big do I make that partition.  How do I clean out the old crud?  I made that partition 16mb.  

I'm not affraid to reinstall Ubuntu, as I just crashed it again 2 nights ago... I'm so new to this, that I'm making mistakes left and right.  ;)

---

### Post by 2pacalypse on 2006-06-17
[QUOTE=headcronie]Here's my problem.  My bios has to have the kernel in the first few MB of the hd or I get the dreaded Grub Error 18.  So, question is this... how big do I make that partition.  How do I clean out the old crud?  I made that partition 16mb.  

I'm not affraid to reinstall Ubuntu, as I just crashed it again 2 nights ago... I'm so new to this, that I'm making mistakes left and right.  ;)[/QUOTE]

i have a wierder prob, if my kernel is in the first blocks of the hdd then right after the ubuntu 6.06 install i get the same error message, but if its not there. after an update he gives me this error. more info in [here](http://www.ubuntuforums.org/showthread.php?t=198385)

---

