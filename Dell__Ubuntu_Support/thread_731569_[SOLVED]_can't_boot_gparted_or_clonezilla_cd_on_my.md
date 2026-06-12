---
title: "[SOLVED] can't boot gparted or clonezilla cd on my 530n"
date: 2008-03-22
forum: Dell  Ubuntu Support
---

### Post by motoperpetuo on 2008-03-22
i just got my 530n with ubuntu preinstalled today. all in all, it seems pretty nice, but i can't get any of the CD-based tools i commonly 
use to boot properly. for example, when i try to boot my gparted CD, i make it to the stage where i select my keymap and then i get this:

>>Determining root device...
>>Determining looptype...
!!Invalid loop location: /gparted.dat
!!Pleas export LOOP with a valid location, or reboot and pass a proper loop=...
!!kernel command line!

i get similar errors when i try to boot my clonezilla CD. both of these CDs work great on my other two computers, which are both around six or seven years old (if that matters). anyone have any idea what i can do to get these CDs to boot and run like they're supposed to?

---

### Post by Aearenda on 2008-03-22
I have a 530 (not 530n) but I doubt there is much difference inside. I can boot OK from a GPartEd/Clonezilla 2.0CD.

It sounds like the SATA CD drive is not being found on your machine, during the CD boots. 

These machines have a driver load race condition that is fixed in the supplied Ubuntu installation - see [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

I suspect you have the same problem occurring during CD boot. It has been suggested that placing the keyboard and mouse in different USB sockets might help - [http://ubuntuforums.org/showthread.php?t=719483](http://ubuntuforums.org/showthread.php?t=719483)

Or you could try booting from a USB CD drive, if you have one. There may well be other ways around this that I am not aware of, using kernel parameters at boot time.

I hope this helps!

---

### Post by motoperpetuo on 2008-03-28
so, i've spent about a week working on this, both on forums and with dell support. so far, the most interesting suggestion i've had from dell was to disconnect my internal SATA hard drive. when i did that, CDs were able to boot normally. obviously, this isn't much of a work around because i'll probably need to boot to my internal hard drive once in a while, but it's still interesting.

i'm thinking of wiping my internal hard drive, if i can find a way to do it. i was thinking that maybe the way dell has it partitioned is causing the problem. the main reason i think this is that with many CDs, it ends up booting to the preinstalled restore partition rather than the CD.

i'll probably have to boot to a windows CD to wipe the hard drive, though. for some reason, windows CDs boot fine. it's the linux CDs that are the problem.

---

### Post by Aearenda on 2008-03-28
I wonder if this casts any light on your problem - try setting the SATA mode to RAID in the BIOS when booting from CD (assuming it hasn't already been tried as a result of your research). [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702)

---

### Post by motoperpetuo on 2008-03-29
So, I deleted all the partitions on the hard drive. I had to use a Windows install CD to do this, because I wasn't able to get Gparted or other Linux CDs to boot. Nevertheless, once I got rid of everything Dell had preinstalled on the hard drive, everything worked fine. I've now installed Linux Mint and imaged my hard drive with Clonezilla.

The only question that remains about this is if anyone else with one of these Dell preinstalled Ubuntu computers has seen such a thing. Who knows, maybe I just got "lucky."

---

### Post by Aearenda on 2008-03-29
I'm glad it all got sorted out in the end - have fun with Linux Mint!

---

