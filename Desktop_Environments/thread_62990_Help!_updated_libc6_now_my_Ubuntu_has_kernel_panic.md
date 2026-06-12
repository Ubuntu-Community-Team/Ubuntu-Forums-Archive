---
title: "Help! updated libc6 now my Ubuntu has kernel panic"
date: 2005-09-06
forum: Desktop Environments
---

### Post by kdavison007 on 2005-09-06
So I did something stupid and updated a debian version of libc6 on my Ubuntu Hoary install not knowing how important this library is. Well, next thing I know I can't run anything. Knowing death was upon the system I rebooted and sure enough, kernel panic. I tried a couple work-arounds involving updating to Breezy initrd and kernel, but I can't get past chrooting my system when using the live CD. I'm following this but after I mount my hard drive (mount /dev/hda1 /mnt/hda1" and run "chroot /mnt/hda1 /bin/bash" I get "chroot: cannot run command `/bin/bash': No such file or directory"

Is there another way around this or another solution?

---

### Post by arnieboy on 2005-09-06
[QUOTE=kdavison007]So I did something stupid and updated a debian version of libc6 on my Ubuntu Hoary install not knowing how important this library is. Well, next thing I know I can't run anything. Knowing death was upon the system I rebooted and sure enough, kernel panic. I tried a couple work-arounds involving updating to Breezy initrd and kernel, but I can't get past chrooting my system when using the live CD. I'm following this but after I mount my hard drive (mount /dev/hda1 /mnt/hda1" and run "chroot /mnt/hda1 /bin/bash" I get "chroot: cannot run command `/bin/bash': No such file or directory"

Is there another way around this or another solution?[/QUOTE]
The reason why u get that is because /bin/bash is indeed not a directory. its an executable. normally u wouldnt wanna mount your hard drive in your /bin directory.
look for any directory that u might have in /media or /mnt and mount it there. 
anyway, i get the feeling u have screwed up your ubuntu install beyond repair. upgrading to the latest libc from debian stable repos was not a suicidal move (I have done it myself) but u gotta make sure u have all the other dependencies installed as well (not just libc). thats what crashed your system.
Updated to breezy initrd? how did u go about doing that?
tell me in detail all that u did to screw ur hoary up and I will help u undo all that as much as possible.

---

### Post by kdavison007 on 2005-09-06
Thanks, Arnieboy.  

Long story short I was trying to use dpkg to install version .18 of myth-frontend.  It failed because it wanted a newer version of libc6.  I found a newer version of libc6 from debian and figured that would be satisfactory.  I ran dpkg on that as well and it gave me the dependancy message.  I reran with the --force-yes option and it seemed to go through.  Next thing I know hell breaks loose in a major way.  Nothing would load and after mucking around with no luck I feared the worse and rebooted.  That's when I received the kernel panic.

The reason I talk about Breezy is because I saw a fix to update /etc/apt/sources for breezy and then do apt-get install initrd and then use dpkg to reconfigure the new kernel.  To do this the fix calls for first booting off the live cd then doing "mount /dev/hda1 /mnt/hda1" to get the drive mounted and then "chroot /mnt/hda1" and then run the apt-get as I stated to get the system upgraded.  Does this sound like a viable fix?  I get stuck on the chroot because it gives that message "chroot: cannot run command  '/bin/bash': No such file or directory"  I even added -w to make it a read and write mount.

---

### Post by arnieboy on 2005-09-06
[QUOTE=kdavison007]Thanks, Arnieboy.  

Long story short I was trying to use dpkg to install version .18 of myth-frontend.  It failed because it wanted a newer version of libc6.  I found a newer version of libc6 from debian and figured that would be satisfactory.  I ran dpkg on that as well and it gave me the dependancy message.  I reran with the --force-yes option and it seemed to go through.  Next thing I know hell breaks loose in a major way.  Nothing would load and after mucking around with no luck I feared the worse and rebooted.  That's when I received the kernel panic.

The reason I talk about Breezy is because I saw a fix to update /etc/apt/sources for breezy and then do apt-get install initrd and then use dpkg to reconfigure the new kernel.  To do this the fix calls for first booting off the live cd then doing "mount /dev/hda1 /mnt/hda1" to get the drive mounted and then "chroot /mnt/hda1" and then run the apt-get as I stated to get the system upgraded.  Does this sound like a viable fix?  I get stuck on the chroot because it gives that message "chroot: cannot run command  '/bin/bash': No such file or directory"  I even added -w to make it a read and write mount.[/QUOTE]

u force-installed a libc deb? lol.. reinstall hoary. period.

---

### Post by kdavison007 on 2005-09-07
Ugh.  Well, at least I can get my important data off using the live CD.  I'm sure there is a way to fix it as I've heard others with libc6 issues being resolved, but I just don't know enough about this library or emergency recovery in linux to do much.  Thanks for the help, though.

---

