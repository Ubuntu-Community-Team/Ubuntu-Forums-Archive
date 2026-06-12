---
title: "Help Linux Dual boot"
date: 2006-05-11
forum: Desktop Environments
---

### Post by sephy on 2006-05-11
I recently started a linux dual boot system with windows XP professional. I have windows XP professional on my 80GB hard drive and plugged in my 10GB hard drive to use for linux. I installed it fine and am using GRUB as the dual boot system. I shut down linux once it first installed and logged on to windows to get linux drivers. I restarted the Computer to go back to linux to install the driver and it starts posting, detects hard drives and where it should ask me for an operating system to load it has a black screen I think the hard drive clicks and the system restarts itself and just keeps restarting at that point. can someone help me remove this problem. I am using an AMD athlon XP processor, 1024MB DR400 RAM and an ECS 741M Motherboard.

---

### Post by yager on 2006-05-18
I hope that you have figured this out by now but just in case.....

First check that the BIOS is set to boot the hard drives in order.  I am assuming the 80G is the 1st drive and the 10 is the 2nd drive.  Also while you are here, check that your CD ROM drive is in boot order before the hard drives.

To rule out some kind of random computer problem, either put your Ubuntu Install CD or a Windows Rescue CD in the CD drive and start the computer.  If the system reacts as expected, then the problem is in the drives.

If you used the Windows Rescue CD, you should be able to run fdisk /MBR to replace the master boot record with a clean copy exactly like windows wants.  Reboot the computer and verify that it boots perfectly fine to Windows XP.  If this works, then you are at least 1/2 way back.

If you use the Ubuntu Install CD and it starts normally, after going through all of the usual hardware recognition it should end up with you on an Ubuntu desktop.  Next go to System>administration>disks and review what drives are being detected on the computer.  The partition tab will tell you what partitions it sees.  If this looks normal, proceed as follows.

Logout of Ubuntu and restart the computer with the same install CD in the CD drive.  Instead of pressing enter at the first choice, type "rescue".  This will give you a way to repair your drive.
Pick the correct device to mount.  It will most likely be something like /dev/discs/disc0/part1.
When you are at the terminal window, press and hold CTRL-Alt-F2.  This will put you in a terminal window.  Type the following lines followed by a return.
mount -tproc proc /target/proc
chroot /target
su

Now try the following command.
grub-install /dev/hda

This will install GRUB to the master boot record of the 80G drive assuming it is the first IDE drive in your system.  Adjust accordingly if you have a SCSI drive.

 Now before you exit, verify that the grub/menu.lst file has your choices present.  Type the following.

vim /boot/grub/menu.lst  (you can use your preferred text editor instead of vim)

This should have opened the menu.lst file that grub uses for you to pick your operating choices from.  Read the comments for some descriptions of what a good menu choice looks like and then scroll down to the bottom to correct any errrors that may exist in the file.  To exit vim, type :s to save your changes or :q to quit with no changes.

Now type exit until you are told that you have exited that shell.
Press Ctrl-Alt-F1 to return to the rescue mode terminal window.
Again type exit.

Remove the CD and allow the computer to reboot.  It should bring up Grub with your menu.  If you made any typos in the menu.lst, don't worry, just go to your choice and type "e", correct the line with the error and then "b" to boot your edited item.

I hope that this corrects your problem if it still exists.

---

### Post by phenolholic on 2006-05-18
Hello - I'm having a GRUB problem too. I had Ubuntu as default on GRUB with XP. I recently installed Red Hat, which also employs GRUB. After installation of redhat, redhat's GRUB (a nice GUI might I add) recognizes windows xp but doesnt let me boot into ubuntu. ubuntu is located on /dev/hda3 on my machine, and I have the command as:

root (hd0,2)
chainloader +1

and this is the message I get:
Error 13: Invalid or unsupported exetucable format

I'd have ubuntu over redhat anyday, but I need to install it to run a 64bit computational chemistry app thats specifically made for red hat.

---

### Post by jones_jj on 2006-05-18
sephy, it really sounds like you may have a bad hard drive.  A way to check this is to unplug both hard drives and just plug in the 80 GB hard drive in and see if it will boot up.  If it does then the drive is working just fine.  Just like it use to.  Next unplug the 80 GB drive and then plug the 10 GB drive in and reboot the PC.  Again if it boots up all is well, but if it does not, then the drive may be bad.  A way to check is to put your Ubuntu CD in the drive and boot up the machine.  Let Ubuntu check the drive and see if there are any bad sectors on the drive.  I have seen this problem before and as I stated it sounds like a bad hard drive.

phenolhic, it sounds like RH's grub loader wrote over your Ubuntu grub loader.  Just follow yager's post on how to fix grub and you should be good to go.

---

### Post by hub_cap on 2006-05-18
My problem is similar to that described earlier, except on my 160GB HD, I have 40GB with WinXP Pro(NTFS), 100GB Storage (NTFS), 5GB (FAT32), 20GB (EXT3), 5GB(swap).
First, I installed BootMagic on the FAT32, then installed Ubuntu on the Linux partition and every thing appeared correctly. I accessed the internet, down loaded some updates, etc. I used the expert mode and did not install a boot loader (thinking that BootMagic would do the job). The BootMagic let me boot into windows using as a first choice, WINNT and second choice Ubuntu. When I rebooted and attempted to use the 2nd choice, I got a message "Loading Ubuntu", but nothing but a black screen appeared. O.K. so much for that.

I then reinstalled Ubuntu and used GRUB. When I rebooted, GRUB gave me first choice of Ubuntu which booted correctly. I rebooted to use the second choice of WinXP, but it would not load XP, only the linux partition worked. I have uninstalled Linux for now and am trying to find a solution without purchasing a machine for the Linux install.:???:

---

### Post by yager on 2006-05-21
[QUOTE=hub_cap]I then reinstalled Ubuntu and used GRUB. When I rebooted, GRUB gave me first choice of Ubuntu which booted correctly. I rebooted to use the second choice of WinXP, but it would not load XP, only the linux partition worked. I have uninstalled Linux for now and am trying to find a solution without purchasing a machine for the Linux install.:???:[/QUOTE]

Since you have removed Ubuntu, it would not be possible to ask you what the grub.conf file looked like.  Its possible GRUB left out a command.

While you are in XP, you could try this example that does not rely on GRUB at all and instead uses the native Windows boot loader.

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)

---

