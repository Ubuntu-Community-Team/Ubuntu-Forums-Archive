---
title: "ubuntu uninstall"
date: 2006-03-01
forum: Desktop Environments
---

### Post by rlittler2001 on 2006-03-01
why is it necessary to use windows to uninstall ubuntu? I've searched for days and days trying to get rid of ubuntu, but found nothing that works. Ubuntu has become a millstone around my life, it's like I got it for free and now I'm stuck with it. This should be a simple process'after all you don't need ubuntu to uninstall windows. Some well meaning person even sugested I use a large magnet since ubumtu is the only thing on my hard drive.

---

### Post by engla on 2006-03-01
Well you don't need windows. I can't even use windows on my box, so it must be possible :-P

You can for example use the LiveCD, open gParted (the partitioning tool) and erase the whole partition with ubuntu.

EDIT: [DON'T try this at home]
I still haven't tried to run "sudo rm -rf /" on a linux box. Rumor has it that the entire disk is wiped. True, or does the rm stop somewhere before that?

---

### Post by bjweeks on 2006-03-01
Just format the harddrive

---

### Post by tadashi on 2006-03-01
[QUOTE=rlittler2001]Some well meaning person even sugested I use a large magnet since ubumtu is the only thing on my hard drive.[/QUOTE]

hahaha that is too funny.  I think that would mess up the hard drive in the process since the magnet (depending on the strength) would pull the metal components of the HDD out of alignment.

I would just delete the partition and then setup 3 partitions.  One is the primary OS (for doing work), 2nd is for data that both partitions can access so FAT32 would be best choice for filing system, and 3rd is your experimental OS.  That way you can blitz one partition without losing any data or productivity.

---

### Post by diogoschneider78 on 2006-03-01
My setup is:

One small partition for Windows, to be able to play Mu Online. Windows is jealous about your PC, so it has to be the first partition. Then a swap partition double the size of your actual RAM and last but not least your Linux partition, for your serious computing needs. Have fun! \\:D/

---

### Post by Jucato on 2006-03-01
The only reason I can think of why you need Windows (specifically the install CD) to uninstall Ubuntu is when you have to restore the Windows Bootloader (NTL...something?). Other than that, I'm pretty sure you don't need it.

---

### Post by incubus on 2006-03-02
Windows or Linux you need a small program that loads the OS when you boot. 

You can erase Ubuntu's partition the method you prefer, but you gotta tell the boot loader that you don't have that OS anymore and what is the default now.

If you have a Windows CD, you just have to boot, go to restore-console mode, and run something like "fixmbr". If you wanna do it the Linux way you have to setup GRUB to call the windows partition. 

Both ways work as expected and are easy to do.

There are tons of how-tos and tutorials on the web about this. But if you're still unsure, tell us your preference and we'll be glad to help you step by step.

incubus

---

### Post by imhdd on 2006-03-06
[QUOTE=rlittler2001]why is it necessary to use windows to uninstall ubuntu? I've searched for days and days trying to get rid of ubuntu, but found nothing that works. Ubuntu has become a millstone around my life, it's like I got it for free and now I'm stuck with it. This should be a simple process'after all you don't need ubuntu to uninstall windows. Some well meaning person even sugested I use a large magnet since ubumtu is the only thing on my hard drive.[/QUOTE]

If trying to completely clean your drive of all formatting, go to your drive manufacturers Website and download their free disk tools and read directions. Tools are small enough to fit on a floppy. The Maxtor and Western Digital tools are excellent. They will test your drive, clean your drive, partition and reformat your drive if you ask  for it.

The only way I've been able to totally clean Linux formatting from drives is with these tools. I usually do a low level format which totally wipes the drive and leaves it with a drive full of zeros which obliterates all previous information from the drive. The low level format is the only way I've found to completely wipe information from the drive and render the information unrecoverable (other than destroying the disks).

I often get used computers with hard drives that still have recoverable personal information on them (even after using a regular reformat). Fortunately for the previous owners, I'm honest. 
I run a low level format on any hard drive that contains sensitive information before I dispose of the drive.

It will certainly clean Linux and allow you to begin again with whatever formatting you want.

---

### Post by batty505 on 2006-03-06
Hey folks
I guess my question is why remove ubuntu?
the more I play with ubuntu, the more I want to leave ms$

the mbr command should work like this
a:\ fdisk /mbr

thats assuming you can get to a win98 bootdisk or cmdline from dos?

or ghost it if you want. I agree theres plenty of wise to fix it.

I find its easier to have a dedicated box for the linux and windows partitions.
forget the multiple OS on 1 drive stuff. get a kvm, some cables and a switch.

besides who wants to mess with partititons after you have your pc configured the way you want?

just my .02 cents

mike

---

### Post by Randomskk on 2006-03-06
[QUOTE=engla]
EDIT: [DON'T try this at home]
I still haven't tried to run "sudo rm -rf /" on a linux box. Rumor has it that the entire disk is wiped. True, or does the rm stop somewhere before that?[/QUOTE]
Entirely true. After I messed this box up beyond no return (deleted a chroot while /home was still mounted there.. ><) I tried it out..
Opened a shell as root (couldn't trust sudo to keep running) then typed that in, hit enter...

It started erasing shit, and then it flagged a LOAD of permission denied messages - my still mounted windows hard disk. Luckily this wasn't erased :P
I yanked the USB stick out right away, without umounting, because a) I didn't think it would unmount but also b) speed was of the essence :P

After it finally finished, I had still got programs running.
However, my machine certainly wasn't stable by this point, so they slowly crashed - and as each one died, it did not come back.

Anyway, after eventually everything quit, I was left in KDE with an empty HDD, so I did the natural thing and hard powered down.

Booted up to GRUB 15 error - it couldn't find where grub was supposed to be on the hard disk ;)
Live disk, lilo and one fix mbr command later, and I was back in windows.

The next day I reinstalled with a determination to not resort to chroots :D

Lesson of the story: really, don't rm -rf / if you have mounted file systems, mounted network drives, mounted removable disks, or anything interesting in your GRUB.
Ah well, it was fun :D

---

