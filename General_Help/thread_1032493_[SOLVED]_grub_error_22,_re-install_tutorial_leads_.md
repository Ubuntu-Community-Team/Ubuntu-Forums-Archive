---
title: "[SOLVED] grub error 22, re-install tutorial leads to error 15"
date: 2009-01-06
forum: General Help
---

### Post by llencelyn on 2009-01-06
Situation background:

I had created a dual-boot setup with Hardy version Ubuntu and Vista. It all worked fine. One day I accidentally installed into root folder, Ubuntu side stops working. Took my system to university Linux Help dept.; told me nothing could really be done. Since I no longer need the Linux system, I was advised to wipe the Linux partitions and re-add them to Vista as a second internal harddrive. I deleted the Linux volumes.

Problems:

When I boot the computer I receive grub error 22.

I searched these forums for help with this and found instructions to reinstall grub using [this]("http://ubuntuforums.org/showthread.php?t=224351") tutorial.

When I type:

"sudo grub

grub> find /boot/grub/stage1"

It returns:

"Error 15: File not found"

Now I'm lost. I greatly appreciate any help that can be provided. If I could entirely eliminate any grub-type loading and just have it automatically boot into Vista, that would be ideal.

---

### Post by Tim Sharitt on 2009-01-06
If you have deleted the linux volume, then you have likely deleted all of the grub files as well. If you do not plan to reinstall linux, you should probably restor your mbr via the Vista install CD.

---

### Post by llencelyn on 2009-01-06
Thank you.

I am days and many miles away from being able to use my Vista CD. Would reinstalling Ubuntu also solve the problem?

---

### Post by Tim Sharitt on 2009-01-06
Yes, it should.

---

### Post by ajgreeny on 2009-01-06
If you can get to a web enabled computer you can get a tool to restore the MBR from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or if you have a ubuntu live CD and a usb disk handy, you can even download the tools you need onto that, and away you go!

---

### Post by llencelyn on 2009-01-06
My attempt to reinstall Ubuntu failed. It suggested I try cleaning my CD...

ajgreeny, thank you for the link to the Windows Recovery. Sadly, I get a message saying no issues could be detected and to check if I have an additional volume mounted - I don't have any USB drives in, but the space that used to contain Linux is there and might be confusing the repair program.

At any rate, I finally was able to get the fdisk -lu command to go. Here are the results:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+  de  Dell Utility
/dev/sda2          194560    21166079    10485760    7  HPFS/NTFS
/dev/sda3   *    21166080   235138736   106986328+   7  HPFS/NTFS
/dev/sda4       235143405   312576704    38716650    5  Extended
/dev/sda5       235143468   309299444    37077988+  83  Linux
/dev/sda6       309299508   312576704     1638598+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

I don't know if that helps, any. I'm going to continue trying things at Super Grub Disk and see what happens.

---

### Post by caljohnsmith on 2009-01-06
You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

---

### Post by llencelyn on 2009-01-06
Ahh! Thank you! It worked - it now boots directly into Windows on startup. I'll definitely not be trying to reintegrate the free space from the Linux volumes anytime soon - or at least until I can get the damn thing backed up and I'm with my Vista recovery materials.

You are officially my hero, caljohnsmith and the Ubuntu support fora!

---

