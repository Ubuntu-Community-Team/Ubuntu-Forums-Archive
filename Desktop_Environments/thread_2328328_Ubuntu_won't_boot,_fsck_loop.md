---
title: "Ubuntu won't boot, fsck loop"
date: 2016-06-20
forum: Desktop Environments
---

### Post by tylersontag on 2016-06-20
Hey all, 

I'm about out of ideas, but i have a 15.10 installation that won't boot.  I tried upgrading this installation to 16.04 a few weeks ago but it failed because my boot partition was full.  Never got around to cleaning up some space and trying again so i'd been running on a partial upgrade for a while.  Well, the other day i noticed the CPU fan was going full throttle but nothing was really running that should be tasking the PC so i tried a reboot.  Afterwards, the PC came up, got past grub, then would show a black screen showing an fsck scan running.  The only problem was that after it sat with some initial fsck information, the screen would black out and start over again.  This loop would repeat ad naseum.

I tried booting up a live CD to check the problem.  I was able to run a full e2fsck on my LVM that houses the OS with no errors.  I'd also noticed i wasn't getting a grub menu, so i tried to do some steps to restore grub but didn't have much luck with that from live cd.  Not really sure what else to try, short of a clean re-install.

---

### Post by grahammechanical on 2016-06-20
An upgrade to a newer version usually removes all previous kernels except one. Was there some problem with 15.10 that you thought an upgrade to 16.04 would solve? What is the actual problem? 15.10 that won't load? An incomplete upgrade to 16.04? An upgrade to the kernel that cannot complete because the boot partition is full? Or a hardware problem?

We can run a Ubuntu live session and at the first purple screen with the icons of a human and a keyboard we can press Enter. At the underlying screen we get these options:

Try Ubuntu without installing
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk.

So, you can test the hard drive and maybe fix what is causing the file system check (fsck) to restart. The live session will also allow you to back up important data. We can also use the Disks utility in the live session and check the Smart data for the hard drive. 

Regards.

---

### Post by tylersontag on 2016-06-20
I think i was staring at the machine too long and forgot about the check disk feature on the boot CD.  I'll give that a shot.

As far as the server setup, all i know is i had a failed upgrade a month ago or so that required a reboot.  After the reboot, i had to run e2fsck to fix the drive to get the system back up.  Its ran fine for a few weeks, but last Thursday i noticed the fans spiking, tried a restart and now it won't boot, displaying the behavior listed above.

On an unrelated note, my boot partition only created with 250MB (on a 2TB drive :-/) so it fills up regularly.  I tried to shrink the partition but am unable to, since its an LVM.  Does anyone have any reasources, if i get this working, that i can look at to resize my LVM from a live CD?

---

### Post by tylersontag on 2016-06-22
So i ran the check disk utility in the live CD and it found no errors... like i mentioned, from a live session i've ran e2fsck against the LVM my OS is on and gotten no issue.

BUT, after booting, after the initial purple OS loading screen i getthe following message, for about 60 seconds, then the screen goes black and the process repeats

fsck from util-linux 2.26.2
/dev/mapper/ubuntu--vg-root: recovering journal
/dev/mapper/ubuntu--vg-root:clean, XXXXXX/ XXXXXXXXXX files, YYYYYYYY/YYYYYYYYYYY blocks

Any ideas?

---

### Post by tylersontag on 2016-06-23
Alright, i finally managed to get into recovery mode and resume a runable session (I had to tap shift at the BIOS screen a number of times to get to the adv. grub screen)
I ctried upgrading and saw that the new kernel included in 16.04 needed 100MB of free space, which i didn't have on my tiny 250MB partition, which i believe was the error i got last time.  So i clean up all but the current kernel and am now upgrading to 16.10.  Ill let you know how that goes.

Just as an aside, if anyone knows a good guide to resizing LVMs on a live CD, let me know, that boot partition needs some space.

---

### Post by tylersontag on 2016-06-23
Yeah, finishing the upgrade to 16.04 worked... found this article too on my other issue
[http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume]("http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume")

---

