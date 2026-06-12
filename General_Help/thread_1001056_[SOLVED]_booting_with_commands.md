---
title: "[SOLVED] booting with commands?"
date: 2008-12-03
forum: General Help
---

### Post by Jammanuser on 2008-12-03
Say...would it be possible (since i can't boot into my wubi install the conventional way, due to a crc error; recovery mode doesn't even work...), for me to boot into Ubuntu 8.10, using the commmand line, i.e. pressing "Esc" after ubuntu to access more boot options, and then pressing "c" after selecting the top boot option? i've already tried this, and so i know that i can get into the command terminal like that without getting the crc error! 

and so i was wondering if there r any commands that i could run...idk, maybe first mounting the root.disk, and then booting into it somehow with a series of commands?

Looking forward to **any** and all replies! ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-03
I've also mounted my root.disk before, **after** the crc error, using a Ubuntu Desktop CD, so i know that i can do that again!

I just need to know a command or series of commands that might allow me to boot into Ubuntu, and get around the crc error!

Looking forward to ANY and ALL replies... :)

-jammanuser

:D

---

### Post by brandon88tube on 2008-12-04
Well, when I had housed my wubi install a while back from a bad driver I installed, I was able to login with just a command line. Don't remember how I did it though.

---

### Post by Jammanuser on 2008-12-04
> **brandon88tube said:**
> Well, when I had housed my wubi install a while back from a bad driver I installed, I was able to login with just a command line. Don't remember how I did it though.

well...THAT helps!!! :) wish u could remember it, lol! ;)

maybe u could **try** remembering it...? :)

Thanks for replying though! 

Cheers! 

-jammanuser

:D

---

### Post by ago on 2008-12-04
> **Jammanuser said:**
> Say...would it be possible (since i can't boot into my wubi install the conventional way, due to a crc error; recovery mode doesn't even work...), for me to boot into Ubuntu 8.10, using the commmand line, i.e. pressing "Esc" after ubuntu to access more boot options, and then pressing "c" after selecting the top boot option? i've already tried this, and so i know that i can get into the command terminal like that without getting the crc error! 

and so i was wondering if there r any commands that i could run...idk, maybe first mounting the root.disk, and then booting into it somehow with a series of commands?

Looking forward to **any** and all replies! ;)

-jammanuser

:D

yes, you can, you have to 

1) load the kernel with the appropriate argument
2) load the initrd

So as a minimum example

kernel (hd0,1)/ubuntu/disks/boot/vmlinuz root=/dev/sda1
initrd (hd0,1)/ubuntu/disks/boot/initrd.gz
boot

Then there are various kernel arguments, some will instruct the kernel to mount a given (host)_device (root=), others allow you to load loop image (loop=...) and other allow you to break the boot process at certain point: (break=mount) or to launch some other command instead of init (init=/bin/sh)

---

### Post by Jammanuser on 2008-12-04
> **ago said:**
> yes, you can, you have to 

1) load the kernel with the appropriate argument
2) load the initrd

So as a minimum example

kernel (hd0,1)/ubuntu/disks/boot/vmlinuz root=/dev/sda1
initrd (hd0,1)/ubuntu/disks/boot/initrd.gz
boot

Then there are various kernel arguments, some will instruct the kernel to mount a given (host)_device (root=), others allow you to load loop image (loop=...) and other allow you to break the boot process at certain point: (break=mount) or to launch some other command instead of init (init=/bin/sh)

ok...cool! its nice to know there **is** a way to boot in with commands...however since i didn't really understand all of what u said, could u please explain urself in clearer terms??? ;)

Thanks, and really appreciate ur help! :)

-jammanuser

:D

EDIT: never mind!!! i think i understand now what u posted...at least the first part, and the part needed to boot! i guess i really don't have to understand the rest for now! Cheers! :D i'll let u know whether it works or not...or if i get the same damn crc error!

---

### Post by magmon on 2008-12-04
Dude, why not uninstall wubi and then make a partition and install ubuntu into it? Its a pretty easy process.

---

### Post by Jammanuser on 2008-12-04
> **magmon said:**
> Dude, why not uninstall wubi and then make a partition and install ubuntu into it? Its a pretty easy process.

uhh...because...I...want...the...CRC error...FIXED! 

HAHAHA!!! :D :D :D :D 

**actually**...i have a couple of programs that i installed on my wubi, which i **built** manually, and it was a long process...and i would rather not have to do it all over again, if u know what i mean! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-04
ago: I tried ur boot commands...but the **first** one didn't even work! i kept getting error 15 (file not found)!

i tried different combinations of it, i.e. "hd0,2" (instead of "hdo,1"), thinking that maybe it was installed on partition #2, instead of 1; "hdO,2" with "sda3" instead of "sda1" since that's where Windows is installed, in my case...and other ones as well, but none of them worked!

i also went to the "boot" folder in Windows, and verified that "vmlinuz" exists...even though the actual file name is longer, i.e. being "vmlinuz-2.6.27-7-generic" instead! so should i try the full filename of vmlinuz instead of just "vmlinuz"?

Looking forward to ur reply... ;)

-jammanuser

:D

EDIT: Ok...so I just tried the **full** filename of "vmlinuz" in place of "vmlinuz"...but it still didn't work! i keep getting error 15 (file not found)!!! I **really** need some help here, guys!!! ANYONE???

---

### Post by Jammanuser on 2008-12-06
Does ANYONE have the answer???? ^^^^^ Feel FREE to respond!!! ):P

Cheers! :)

-jammanuser

:D

---

### Post by azmo35 on 2008-12-06
Hi,see this site may help: [http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check) crc error.Sorry maybe this one [http://bbs.archlinux.org/viewtopic.php?id=36512](http://bbs.archlinux.org/viewtopic.php?id=36512)

---

### Post by Jammanuser on 2008-12-06
> **azmo35 said:**
> Hi,see this site may help: [http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check) crc error.Sorry maybe this one [http://bbs.archlinux.org/viewtopic.php?id=36512](http://bbs.archlinux.org/viewtopic.php?id=36512)

Thanks, dude...but i **really** didn't need to know what a crc error was/is...i needed to know how to **fix** it!!! :D

Cheers! ;)

-jammanuser

:D

EDIT: Thanks! lol, i'll be SURE to check it out!

---

### Post by azmo35 on 2008-12-06
Sorry about that, but i read maybe is bad ram.

---

### Post by Jammanuser on 2008-12-06
hmm...it appears this MAY work! ;) although the crc error on that page was slightly different...mine didn't wait to say "uncompressing Linux" before giving the crc error...so i'm not sure if the solution will work for me or not!

I'll try and let everyone here know whether or not it works! :)

Cheers! ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
> **azmo35 said:**
> Sorry about that, but i read maybe is bad ram.

Nope...my Ram's not the issue here! :D My computer is practically brand-new, with 4GBs of memory! No WAY that my Ram's the problem here! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
I also noticed that the "solution" is for ArchLinux...NOT Ubuntu! But I'll try it anyway, and let u know if it works... ;)

Cheers!  :)

-jammanuser

:D

---

### Post by azmo35 on 2008-12-06
:-k I'm not in any way teach anything, but I found reference to crc error,then i thought share.About the ram maybe less ram or run a test 	
through live cd may help [http://www.hardforum.com/showthread.php?t=1055110](http://www.hardforum.com/showthread.php?t=1055110) post 8 and 9 Thanks.AZMO

---

### Post by Jammanuser on 2008-12-06
> **azmo35 said:**
> :-k I'm not in any way teach anything, but I found reference to crc error,then i thought share.About the ram maybe less ram or run a test 	
through live cd may help [http://www.hardforum.com/showthread.php?t=1055110](http://www.hardforum.com/showthread.php?t=1055110) post 8 and 9 Thanks.AZMO

well...thanks for sharing!!! :D although i **really** don't think that fixes my problem, though... ;) Again, the Ram is not the issue here, and i've already ran a filesystem check using the LiveCD...but it didn't fix the problem! 

Cheers! :)

-jammanuser

:D

---

### Post by balaknair on 2008-12-06
Hi
I doubt if the ArchLinux guide is going to help much, since it's not a virtual image there.
In your case(from what I could make out after reading through the many threads you've started about wubi :D and from the Launchpad bug report you filed), I thought of three possibilities 
a) Corrupted MBR/ MBR entry- unlikely because you get up to the point where it tries to load the vmlinuz kernel, but still a possibility.
b) Corrupted virtual disk image- but I think you mentioned being able to mount the virtual disk from a LiveCD boot and running a file check on it.
c) Corrupted sectors within the virtual disk image file as a result of the power reset- specifically sectors corresponding to where the initrd or kernel or similar crucial files are located- though this should show up on running chkdsk on Vista.

So far I haven't come across a fix for this anywhere. Sorry about that. I also doubt there can be any fix for data corruption caused by a hard reboot. The best option would possibly be creating a Recovery Floppy or CD to restore the MBR, and a backup of the drive image(root.disk), though I doubt anyone just looking to give Ubuntu a casual try via Wubi would set aside 5-10 GB just for a backup.

One thing that occured to me(please keep in mind that Wubi is not my forte, and this is me guessing/hypothesising) is that it's a virtual drive image, right? So *if* it's not corrupted/altered(as evidenced by the chkdsk results), it's got to be something either in the MBR or someplace else outside the disk image(maybe the Windows registry(?) or the NTFS partition headers). This should be fixed by a new Wubi install.
So considering Wubi works a bit like Virtualbox(Virtual OS settings and data in one place, and the Virtual disk image(.vdi file) in another), maybe there's some crucial symlink or similar entry somewhere that's been trashed? In that case you might try something like this- make a backup copy of the .disk file in C:\Ubuntu... and then uninstall Wubi from Windows---> reinstall Wubi---> once you have a new install of Wubi Ubuntu, and you have verified that it works, try replacing the new root.disk image and replace it with the one you backed up earlier---> Try booting again and see if Ubuntu boots up normally. If not, at least you'll be able to recover any important stuff from your previous install.

To be absolutely honest with you, this is just stuff that is based on my assumption  of how Wubi would work, though I think the Wubi wiki does say you can recover files this way- "Old installation files can be mounted within Ubuntu and any relevant data can be copied over the new installation. "
[https://wiki.ubuntu.com/WubiGuide#Can%20I%20back%20up%20the%20installation%20files?](https://wiki.ubuntu.com/WubiGuide#Can%20I%20back%20up%20the%20installation%20files?)

There were also some other guides there, but I assume you'd have tried those by now.

Other than that, I'm sorry I haven't been able to help more. Wishing you luck.

---

### Post by balaknair on 2008-12-06
Oh, and one other thing, don't be too sure about your RAM being fully functional just because it's new. I've seen RAM modules, GPU cards, and HDDs(not to mention motherboards) fail while brand new, often fried by power fluctuations directly or as a result of abrupt power loss when it fries the UPS(and a hard reboot often has the same effect as a sudden power loss followed by a sudden increase in voltage across your motherboard, a good PSU and mobo with good ACPI support can mitigate this for hard reboots, but there's also an element of luck- like a parachute not opening, it has to go wrong only once)..
I'm not saying RAM damage *is* the cause here, but don't rule it out till you've done a memtest(not a filesystem check).

---

### Post by Jammanuser on 2008-12-06
> **balaknair said:**
> Hi
I doubt if the ArchLinux guide is going to help much, since it's not a virtual image there.
In your case(from what I could make out after reading through the many threads you've started about wubi, and from the Launchpad bug report you filed), I thought of three possibilities 
a) Corrupted MBR/ MBR entry- unlikely because you get up to the point where it tries to load the vmlinuz kernel, but still a possibility.
b) Corrupted virtual disk image- but I think you mentioned being able to mount the virtual disk from a LiveCD boot and running a file check on it.
c) Corrupted sectors within the virtual disk image file as a result of the power reset- specifically sectors corresponding to where the initrd or kernel or similar crucial files are located- though this should show up on running chkdsk on Vista.


a) possible, but not likely!
b) yes, i HAVE managed to mount my virtual disk before with the LiveCD, and already recovered my files...which is why the "crc error" continues to puzzle me! if i can MOUNT the root.disk just fine, and access all my files, why can I not then boot into Ubuntu??? Of course i know that the boot files probably have nothing to do with being able to mount the virtual disk or not...but STILL!!! 
c) possibly...although i've run a filesystem check on the virtual disk itself before, but the only error it found (and fixed!) was a missing "journal" which it recovered...but i could still not boot! and I have also checked already, and verified that the "initrd", "vmlinux", and other important boot files ARE there! and I've also already tried running a disk check (chkdsk /r) as well, but it apparently did more HURT than good, because after the disk check, i was able to boot into Vista again, the FIRST time, but it froze that time at startup, and so i hard rebooted AGAIN (sorry...i had no other choice!), and then i was no longer able to get into Vista again, at ALL, until after i ran "startup repair" which fixed the boot problem into Vista, but i could still not boot into Ubuntu! 

> 
So far I haven't come across a fix for this anywhere. Sorry about that. I also doubt there can be any fix for data corruption caused by a hard reboot. The best option would possibly be creating a Recovery Floppy or CD to restore the MBR, and a backup of the drive image(root.disk), though I doubt anyone just looking to give Ubuntu a casual try via Wubi would set aside 5-10 GB just for a backup.
 

hmm...good idea! i'll back up the root.disk like u said...as for the creating a Recovery Floppy or CD, i don't have a floppy drive, and have no IDEA where to get the recovery files needed to create a CD! ;) Cheers! 
> 
One thing that occured to me(please keep in mind that Wubi is not my forte, and this is me guessing/hypothesising) is that it's a virtual drive image, right? So *if* it's not corrupted/altered(as evidenced by the chkdsk results), it's got to be something either in the MBR or someplace else outside the disk image(maybe the Windows registry(?) or the NTFS partition headers). This should be fixed by a new Wubi install.
So considering Wubi works a bit like Virtualbox(Virtual OS settings and data in one place, and the Virtual disk image(.vdi file) in another), maybe there's some crucial symlink or similar entry somewhere that's been trashed? In that case you might try something like this- make a backup copy of the .disk file in C:\Ubuntu... and then uninstall Wubi from Windows---> reinstall Wubi---> once you have a new install of Wubi Ubuntu, and you have verified that it works, try replacing the new root.disk image and replace it with the one you backed up earlier---> Try booting again and see if Ubuntu boots up normally. If not, at least you'll be able to recover any important stuff from your previous install.

To be absolutely honest with you, this is just stuff that is based on my assumption  of how Wubi would work, though I think the Wubi wiki does say you can recover files this way- "Old installation files can be mounted within Ubuntu and any relevant data can be copied over the new installation. "
[https://wiki.ubuntu.com/WubiGuide#Can%20I%20back%20up%20the%20installation%20files?](https://wiki.ubuntu.com/WubiGuide#Can%20I%20back%20up%20the%20installation%20files?)

There were also some other guides there, but I assume you'd have tried those by now.

Other than that, I'm sorry I haven't been able to help more. Wishing you luck.

hmm...those r VERY good ideas! :D backing up the root.disk, and then reinstalling Wubi will solve the problem (if it fixes the CRC error, that is!) of me not wanting to lose the stuff on the current Wubi install! i'm surpised i didn't think of that before! :o Thanks! as for what u suggested concerning the Windows registry maybe being the cause of the error...hmm, don't think so! i have already tried different "Registry fix" programs (specifically, Registry Fix 7, and RegCure...two of the highest ranking registry fixing programs in the reviews!), thinking along those lines as well, but it didn't fix my problem! Cheers, though! ;) It was a nice thought! :D 

I think i AM going to try that, and i'll let u know whether or not it works! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
> **balaknair said:**
> Oh, and one other thing, don't be too sure about your RAM being fully functional just because it's new. I've seen RAM modules, GPU cards, and HDDs(not to mention motherboards) fail while brand new, often fried by power fluctuations directly or as a result of abrupt power loss when it fries the UPS(and a hard reboot often has the same effect as a sudden power loss followed by a sudden increase in voltage across your motherboard, a good PSU and mobo with good ACPI support can mitigate this for hard reboots, but there's also an element of luck- like a parachute not opening, it has to go wrong only once)..
I'm not saying RAM damage *is* the cause here, but don't rule it out till you've done a memtest(not a filesystem check).

hmm...its a thought...although i've already tried (like i mentioned in one of my other threads!) a memtest! admittedly, i didn't let it finish, because i didn't have the patience to wait 5 damn hours for the memtest to complete running...and then tell me it found no errors! ;) and additionally, if it WAS my RAM that's the source of of all my misery...then why would i be able to boot into Vista fine, then? :D

it seems to me that IF it was the Ram, that i wouldn't be able to boot into either one! ubuntu OR Vista! ;)

Cheers! :)

-jammanuser

:D

---

### Post by balaknair on 2008-12-06
OK, I've been reading up on some stuff about how Loopback Root Filesystems work. It seems getting a crc error is usually the result of a corrupted kernel image.
Ergo, a new kernel image must be compiled, ie, a reinstall with Wubi.
So, apparently, the MBR is unaffected(since it gets as far as starting to load the kernel). As is the root.disk file.
I think there should be kernel and initram files or folders within the C:\Ubuntu folder.
I was unable to find in depth documentation on the inner workings of Wubi that I could understand, so I'm not sure about the exact filenames in use with Wubi.
Start up would probably go something like this BIOS> boot.ini> The modified boot.ini points to the linux loader _which initiates the kernel> kernel loads into RAM and initramd is copied into RAM_> The mounted kernel running from the RAMdisk now mounts the disk image(root.disk) using linuxrc > The file structure within the root.disk is set as the loopback device> now the loopback device is booted as root / and now boots normally while initramd are all offloaded from RAM> Ubuntu boots from Wubi.

So from what I understand your crc error happens in the underlined portion above, even one or two bad sectors here or even a slight change can put a stop to things. Which I think can be fixed by reinstalling Wubi and replacing the new root.disk file with your backed up copy. This is not unique to Wubi, I've had it happen on an Ubuntu 7.04 full install on ext3 before. The solution I followed there was reinstall the OS on / while retaining my /home which was on a separate partition(thanks to aysiu and his Ubuntu guides at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) ). With hindsight, that was pretty similar to this.

And at the end of all this(I've read pages and pages about Wubi and understood just a few paragraphs, and I've come across so much information about how Wubi on FAT/NTFS is so much more vulnerable to hard reboots and my head is beginning to throb now) I'm grateful that I've always opted for a dual boot option with Ubuntu on its own ext3 partition.

I hope at least some of this was helpful.
I'm all tuckered out now(it's 2:30 AM here now in India and I'm having trouble keeping my eyes open), so I think I'll go to bed. I doubt if I can help you any more than this anyway. So I'll sign off now, and wish you luck. If you do find a definitive solution, do post it here(just academic interest, though I guess it'll come in handy for a lot of others).

All the best

---

### Post by balaknair on 2008-12-06
> **Jammanuser said:**
> hmm...its a thought...although i've already tried (like i mentioned in one of my other threads!) a memtest! admittedly, i didn't let it finish, because i didn't have the patience to wait 5 damn hours for the memtest to complete running...and then tell me it found no errors! ;) and additionally, if it WAS my RAM that's the source of of all my misery...then why would i be able to boot into Vista fine, then? :D

it seems to me that IF it was the Ram, that i wouldn't be able to boot into either one! ubuntu OR Vista! ;)

Cheers! :)

-jammanuser

:D
Yes I remember reading that post, and I also remember you said you aborted that test, that's why I specified memtest, instead of filesystem check. 
I'm not suggesting that a RAM error is the cause of your crc error, I doubt that's the case. I'm just suggesting(advising?) that you don't take for granted that just because it's new, your RAM(and other hardware) is functioning properly. I speak from personal experience as well as that of friends and family for whom I've done a bit of PC troubleshooting and/or maintenance. Hard reboots are very, very rough on your hardware, and in spite of it being called *hard*ware, most components are actually pretty fragile. Thus spake the man who has lost 20GB worth of music files(ripped from CDs on many a sleepless night over a period of 8 months) when his hard drive gave up the ghost(my fault, I ignored the frequent whirrr-click sounds from the drive and the long boot times I'd been getting over the past couple of weeks). I've also had boot failures from faulty RAM. Of course this was way back, pre-ubuntu, whilst using Win2K and WinXP, and hardware has gotten better. But always play it safe, especially regarding hard reboots(Avoid whenever possible, try to check every bit of critical hardware after a hard reboot and backup important files ASAP).

Just saying):P

---

### Post by Jammanuser on 2008-12-06
> **balaknair said:**
> OK, I've been reading up on some stuff about how Loopback Root Filesystems work. It seems getting a crc error is usually the result of a corrupted kernel image.
Ergo, a new kernel image must be compiled, ie, a reinstall with Wubi.
So, apparently, the MBR is unaffected(since it gets as far as starting to load the kernel). As is the root.disk file.
I think there should be kernel and initram files or folders within the C:\Ubuntu folder.
I was unable to find in depth documentation on the inner workings of Wubi that I could understand, so I'm not sure about the exact filenames in use with Wubi.
Start up would probably go something like this BIOS> boot.ini> The modified boot.ini points to the linux loader _which initiates the kernel> kernel loads into RAM and initramd is copied into RAM_> The mounted kernel running from the RAMdisk now mounts the disk image(root.disk) using linuxrc > The file structure within the root.disk is set as the loopback device> now the loopback device is booted as root / and now boots normally while initramd are all offloaded from RAM> Ubuntu boots from Wubi.

So from what I understand your crc error happens in the underlined portion above, even one or two bad sectors here or even a slight change can put a stop to things. Which I think can be fixed by reinstalling Wubi and replacing the new root.disk file with your backed up copy. This is not unique to Wubi, I've had it happen on an Ubuntu 7.04 full install on ext3 before. The solution I followed there was reinstall the OS on / while retaining my /home which was on a separate partition(thanks to aysiu and his Ubuntu guides at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) ). With hindsight, that was pretty similar to this.

And at the end of all this(I've read pages and pages about Wubi and understood just a few paragraphs, and I've come across so much information about how Wubi on FAT/NTFS is so much more vulnerable to hard reboots and my head is beginning to throb now) I'm grateful that I've always opted for a dual boot option with Ubuntu on its own ext3 partition.

I hope at least some of this was helpful.
I'm all tuckered out now(it's 2:30 AM here now in India and I'm having trouble keeping my eyes open), so I think I'll go to bed. I doubt if I can help you any more than this anyway. So I'll sign off now, and wish you luck. If you do find a definitive solution, do post it here(just academic interest, though I guess it'll come in handy for a lot of others).

All the best

Hey...thanks for all ur help! :D I really appreciate it, yo! and those were some REALLY good ideas u came up with...and which **may** have solved my problem...don't know yet, because i haven't tried it...yet! ;)

Cheers, and i'll let u know if ur suggestion worked or not! Thanks, and good night to u! Say hello to all the people in India for me... ;)

Cheers! :D

-jammanuser

---

### Post by Jammanuser on 2008-12-06
> **balaknair said:**
> Yes I remember reading that post, and I also remember you said you aborted that test, that's why I specified memtest, instead of filesystem check. 
I'm not suggesting that a RAM error is the cause of your crc error, I doubt that's the case. I'm just suggesting(advising?) that you don't take for granted that just because it's new, your RAM(and other hardware) is functioning properly. I speak from personal experience as well as that of friends and family for whom I've done a bit of PC troubleshooting and/or maintenance. Hard reboots are very, very rough on your hardware, and in spite of it being called *hard*ware, most components are actually pretty fragile. Thus spake the man who has lost 20GB worth of music files(ripped from CDs on many a sleepless night over a period of 8 months) when his hard drive gave up the ghost(my fault, I ignored the frequent whirrr-click sounds from the drive and the long boot times I'd been getting over the past couple of weeks). I've also had boot failures from faulty RAM. Of course this was way back, pre-ubuntu, whilst using Win2K and WinXP, and hardware has gotten better. But always play it safe, especially regarding hard reboots(Avoid whenever possible, try to check every bit of critical hardware after a hard reboot and backup important files ASAP).

Just saying):P

Ok...cool! i'll definitely take that under consideration then...although Vista has a way of FORCING one to hard reboot! ;) Again, thanks for all ur help!

Cheers! ):P

:D

---

### Post by Jammanuser on 2008-12-07
I'm reinstalling Wubi right now!!! :D I'll let u know if it works or not! ;)

Cheers! :)

-jammanuser

:D

P.S. do u happen to know the commands to change the ISO that Wubi uses, when it installs? i want to use the ISO that i ALREADY have, so i don't have to spend so much time (again!) waiting for it to finish downloading the 699 MB file! Thanks in advance... :)

---

### Post by balaknair on 2008-12-07
I think you just need to place the downloaded iso in the same folder as the wubi.exe file when you run wubi.

You can also burn the iso to a CD(or mount the iso image with something like daemon tools or virtual cd), and run wubi from the CD, since the CD already has Wubi on it.

---

### Post by ilikepancakes on 2008-12-07
> **azmo35 said:**
> Hi,see this site may help: [http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check) crc error.Sorry maybe this one [http://bbs.archlinux.org/viewtopic.php?id=36512](http://bbs.archlinux.org/viewtopic.php?id=36512)

Please stop sending assholes to the Arch Linux Forums. See:


[http://bbs.archlinux.org/viewtopic.php?id=60377](http://bbs.archlinux.org/viewtopic.php?id=60377)
[http://bbs.archlinux.org/viewtopic.php?id=60415](http://bbs.archlinux.org/viewtopic.php?id=60415)
[http://bbs.archlinux.org/viewtopic.php?id=60418](http://bbs.archlinux.org/viewtopic.php?id=60418)
[http://bbs.archlinux.org/viewtopic.php?id=60419](http://bbs.archlinux.org/viewtopic.php?id=60419)

Thank you.

---

### Post by balaknair on 2008-12-07
> **ilikepancakes said:**
> Please stop sending assholes to the Arch Linux Forums. See:


[http://bbs.archlinux.org/viewtopic.php?id=60377](http://bbs.archlinux.org/viewtopic.php?id=60377)
[http://bbs.archlinux.org/viewtopic.php?id=60415](http://bbs.archlinux.org/viewtopic.php?id=60415)
[http://bbs.archlinux.org/viewtopic.php?id=60418](http://bbs.archlinux.org/viewtopic.php?id=60418)
[http://bbs.archlinux.org/viewtopic.php?id=60419](http://bbs.archlinux.org/viewtopic.php?id=60419)

Thank you.

I'm not sure just what you're trying to say, so I'll just ask you straight out- what's bugging you? I'm not being snarky, I really don't get it, so please be more lucid, rather than resort to invective. [-(
All four links you posted above(by way of explanation?) are invalid. So that doesn't make things any clearer. :confused:

---

### Post by ilikepancakes on 2008-12-07
I guess you have to be a registered user in order to see those specific parts of the Arch Linux Forums. I'll do some copy/pasta instead:

Thread title: I have a SLIGHT problem...
Author: Jammanuser
First post:

> Do u wanna know what it is???

ArchLinux SUCKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! lol


HAHAHAHAHAHAHAHAHAAHAHAHA!!!!!!!!!!!!!!!!!!!!!!!! lol

and guess what? so do all the people that use this SHITTY distro!!!!!!!!!!! The WISE ones use Ubuntu...

Thread title: I have a problem with my kernel...
Author: Jammanuser
First post:

> Hey...*************! go ahead and send THIS one to the "Dust Bin"!!!! lol

Arch Linux sucks, as do all that use it...

big_smile

Thread title: I am having a slight problem...
Author: Jammanuser
First post:

> I haven't been BANNED yet!!!! so GO ahead and ban me....i was leaving anyway!!! tongue

HAHAHAHA!!!!!!!! lol

I'm a troll, troll, troll, troll, troll...SO WHAT THE **** is anyone going to do about it???? y'all SUCK!!!!!

---

### Post by balaknair on 2008-12-07
> **ilikepancakes said:**
> I guess you have to be a registered user in order to see those specific parts of the Arch Linux Forums. I'll do some copy/pasta instead:

Thread title: I have a SLIGHT problem...
Author: Jammanuser
First post:



Thread title: I have a problem with my kernel...
Author: Jammanuser
First post:



Thread title: I am having a slight problem...
Author: Jammanuser
First post:
Hmmmm...

I understand now why you were so pissed off. That was immature of him. 

I've seen posts by trolls  here on Ubuntuforums too, and they can really spoil one's mood. Such a waste of time. So I offer my condolences(and apologies on his behalf).

Have a nice day.

---

### Post by SBDxAric on 2008-12-07
Umm these kinds of errors are really what make me rethink my installation.........

---

