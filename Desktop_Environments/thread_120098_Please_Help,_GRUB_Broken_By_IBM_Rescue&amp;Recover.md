---
title: "Please Help, GRUB Broken By IBM Rescue&amp;Recovery"
date: 2006-01-20
forum: Desktop Environments
---

### Post by stardotstar on 2006-01-20
OK, I have been powering ahead on my ThinkPad R51 with Ubuntu for a while now - and kept my XP Partition for work (fair enough it is a work computer :roll: ) but having spent most of my time in Linux for the last year or so I had ignored updating the XP side of things.  So getting short on space and less productive at  work I decided to do some cleaning up in XP.

I used the IBM Download Manager to check all the onboard drivers etc.  This has always worked fine for me but this time after installing everything just fine I let it update the "IBM Rescue and Recovery Manager" upon reboot all I get is:

BIOS boot splash, pause
GRUB_

(that is the text GRUB and a flashing cursor on a black screen)  There does not seem to be any key or function I can do to prevent this hang.

I dimagine that the XP IBM tool has installed something on the MBR but I am at a loss to know how to get my GRUB back.  

I cannot afford to lose these partitions - neither the Ubuntu or Windows ones.

Is there some straightforward way I can get a boot cd rom ISO loaded that has a vanilla grub I can attempt to load my two systems with (have to figure out the disk partitions and chainloader etc) and then restore the MBR?

Help really appreciated.  In the mean time I will go hunting on the web for solutions in FAQs and at the GRUB site.

Will

---

### Post by o_fortuna on 2006-01-20
You can restore Grub by following the instructions here: [RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")

---

### Post by Sef on 2006-01-20
>  upon reboot all I get is:

BIOS boot splash, pause
GRUB_

Reinstalling grub should do the trick.  Here's how:

> A Simplistic Approach

Boot with your Ubuntu installation CD 

On the  boot:  prompt, type  rescue  and hit enter 

Follow the instructions on the screen 

When the computer is ready, assuming that  /dev/hda  is where your  /boot  is located, type 

grub-install /dev/hda

Your Grub is now supposed to be recovered. 

Take a look at the  Configuring the GRUB Menu  section of this wiki page

Link: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28GRUB%29%7C%28Reinstall%29]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28GRUB%29%7C%28Reinstall%29")

---

### Post by stardotstar on 2006-01-20
Thanks guys,  I have managed to get XP to boot with the detection of the Grub Super Disk which I made an ISO of on my PC.

I also tried to use that tool to reinstall GRUB which did not work and to detect /boot to boot linux and that did not find any linux either.

I can't remember exactly what my menu.lst looked like since I partitioned this disk so long ago and have had no trouble.

The windows volume manager sees things like this:
Disk 0 C: 24.41 GB NTFS, D: 6.83GB FAT 32, 289MB Unknown, 5.73GB Unknown

So I am assuming that my root is the Fourth Partition of the first (and only disk) - hda? and that the 289MB is either my Swap or /boot???

I am going to try and do the fix using the rescue method of my Ubuntu CD...

Thanks for the help so far.

Will

---

### Post by stardotstar on 2006-01-20
OK I got in by selecting the command line in grub super disk [c]

and setting:

root (hd0,2) which was my ext2fs partition type 0x83

then managed to get the original menu.lst kernel initialisation line with 

cat /boot/grub/menu.lst

and booted successfully with

kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro 
initrd   /boot/initrd.img-2.6.12-10-386
boot

Now I am going to try and reinstall grub from here.

/sbin/**grub**-install /dev/hda

hope all goes well...

---

### Post by stardotstar on 2006-01-20
Whooo, recovered, thanks guys, another great learning experience.

This forum is terrific that you can ask for hints and prompts that bump your l4earning along without feeling self conscious.

Thanks again for the help and prompting.

Will

---

