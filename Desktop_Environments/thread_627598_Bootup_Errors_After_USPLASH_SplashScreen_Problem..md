---
title: "Bootup Errors After USPLASH SplashScreen Problem."
date: 2007-11-30
forum: Desktop Environments
---

### Post by Empire2500 on 2007-11-30
Hello everyone,I'm new here,but I did on occasion lurk around for answers ;D

Here's the story:

Im running a Linux Mint codename Celena System with GNOME desktop. I dont know the exact versions of them (I know that Linux Mint is Ubuntu).
NOTE:The Linux Mint is my MAIN OS,on the main hard drive.I dont have another WINXP boot option or anything..

So Im browsing around on gnome-looks.org,and I fall upon a good looking splash screen.Now normally on Windows I wouldve been able to install it and run it like a charm,but when it came to Ubuntu,I looked for instructions.


Now the splashscreen in question is the following: [http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)


and the Guide is here: [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

I followed all the instructions (installing the newest Alpha [and neglecting the stable..stupid,stupid]) and everything seemed to be succesful,no errors whatsoever.

Now I want to test out my SplashScreen right?

So I restart the computer,the boot option being
  [SIZE="4"]
[COLOR="Red"]root=/dev/sda1/ro quiet splash vga=791[/COLOR][/SIZE]

(vga=791 being the new kernel line entry)
So I boot with that,and all I get is a blank screen..not even the login window loads..just a blank screen
 
So to try and fix this..I decide to take off the vga=791 from the boot options menu,and try that..getting this error  

[SIZE="4"][COLOR="Red"]root (hd0,0)
    Filesystem type is ext2fs, partition type 0x83
  kernel  /boot/vmlinuz-2.6.20-150-generic   root=/dev/sda1 ro quiet splash
                [Linux bzImage, steup=0x1c00, size=0x1a82cc]
  initrd /boot/initrd.img-2.6.20-15-generic
  boot
  [    150.072528] Kernel panic - not syncing: VFS:Unable to mount root fs on unknown-block(0,0)
  [    150.72622]
[/COLOR][/SIZE]
So then I try booting up again,and to my short lasting joy , I see the recovery mode.I try that,the root option being 
[code=] root=/dev/sda1 ro single [/code]

So then I get a bunch of errors preceding with numbers like [43.484028]

The last errors being:

[SIZE="4"][COLOR="Red"]
[   43.483958] VFS:Cannot open root device "sda1" or unknown block(0,0)
[   43.484028] Please append a correct "root=" boot option
[   43.484070] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)
[   43.484120] (blank)  [/COLOR][/SIZE]

So now I don't what to do,I have the LIVECD, what do I do..can I fix this without reinstalling ..AND have the same splash?

Heres my Menu.lst and Device.map just in case (you have to use Linux to open them obviously)
[http://files-upload.com/files/651170/Device Map](http://files-upload.com/files/651170/Device Map)
[http://files-upload.com/files/651183/Menu list](http://files-upload.com/files/651183/Menu list)


I couldnt find another way to show them except by uploading them..being on another computer with WINXP.

I hope there's a solution.
Thanks :)

---

### Post by TeaSwigger on 2007-11-30
At the risk of rudeness (none intended), does Linux Mint not have their own support forums? You may be better off getting specific help there.

I'm not an expert by any stretch but it sounds like you've accidentally messed up your /boot/grub/menu.lst. You should have made a backup before making any changes. If you did, use the live CD to go in and restore it. If you didn't, take this as a lesson ;) and you can reinstall GRUB only from the live CD. That'd let you fix it without having to reinstall the rest of your system. I don't have any links for how to do that handy but it's been covered a number of times here and a search might scare it up. I can't attempt to offer anything specific since files-upload absurdly tells me "Sorry. You can not download this file today. Download traffic for your country is empty."

---

