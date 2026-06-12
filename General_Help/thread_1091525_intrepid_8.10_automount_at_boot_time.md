---
title: "intrepid 8.10 automount at boot time"
date: 2009-03-09
forum: General Help
---

### Post by 3Miro on 2009-03-09
Hi everyone,

I have been having a strange problem after upgrading to 8.10 on both Ubuntu and Kubuntu. I cannot auto-mount my hard drive partitions at boot.

I tried Mount Manager, it sets up correct fstab and then mounts all partitions where I tell it and it works until I reboot. After reboot, fstab has changed with only / and swap mounted.

I tried manually changing fstab and it works until reboot.

I tried both /dev/sd(whatever) and UID and both work until reboot.

After each boot, fstab was cleared to some default setting. Does anyone know why?

---

### Post by kanikilu on 2009-03-09
Can you post your /etc/fstab? Also, this is going to sound like a dumb question, but are you by any chance accidentally booting into a live session with the CD or a USB drive?

I had some automounting trouble myself, but fixed it after switching to UUID's.

I can't really think of any reason why fstab would be overwritten. Have you tried:

- edit fstab
- *sudo mount -a*
- check to see that they were mounted successfully with *mount*
- reboot

Someone reported a similar sounding bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282997](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282997)

But he says it was fixed (not sure if that means it fixed itself with an update, or if he did something to fix it).

---

### Post by computerjunkie on 2009-03-09
With ubuntu I've found I've had to manually mount my hard drive partitions. I suppose you could set up a start up script with sudo mount /dev/sda[whatever]

---

### Post by kanikilu on 2009-03-09
> **computerjunkie said:**
> With ubuntu I've found I've had to manually mount my hard drive partitions. I suppose you could set up a start up script with sudo mount /dev/sda[whatever] This shouldn't be necessary (but maybe it can be used as a last-ditch workaround if all else fails). I've used fstab to automount internal drives and external drives on multiple computers with no problems.

On the machine I'm on now, I mount an external USB drive, the line in fstab is > UUID=6975ad8e-561b-4ac7-8613-caac907c8c66       /media/vault    ext3    rw,user,auto,relatime    0       0

---

### Post by 3Miro on 2009-03-09
I only dual-boot winXP and kubuntu 8.10. It gave me the same trouble in just Ubuntu (64-bit, I have not tried 32-bit, kubuntu 8.04 on both 64 and 32 used to work fine). I am only booting from my hard-drive, no LiveCD no USB.

Current /etc/fstab:

> 
proc /proc proc defaults 0 0
UUID=04f2e089-6565-4f00-a516-ca8b1f60f7fe / ext3 relatime,errors=remount-ro 0 1
UUID=c63eacf3-3b2e-4694-9b14-05aabdaa67ea none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


Mount Manager overwrites this with:
> 
/dev/scd0    /media/cdrom0    udf,iso9660    noauto    0    0
UUID=BEB8DF05B8DEBADB    /media/winc    ntfs    defaults    0    0
UUID=c63eacf3-3b2e-4694-9b14-05aabdaa67ea    swap    swap    sw    0    0
UUID=04f2e089-6565-4f00-a516-ca8b1f60f7fe    /    ext3    defaults    0    1
UUID=9840EB8640EB6988    /media/StorageWin    ntfs    defaults    0    0
UUID=2961e9a5-3258-4a07-a4ae-33a5a0ec6a60    /media/StorageLinux    ext3    defaults    0    0


I double-check, indeed the above is the new fstab, but upon reboot it reverts back to the original version with only / and swap.

I tried manually editing the fstab with /dev/sd** in place of UUID, works for the time being, but upon restart fstab reverts to original form.

I tried generating the fstab file with Mount Manager, save it to a separate file and then sudo copy it to /etc/fstab. Works until reboot.

For the time being I have added to rc.local some manual mount commands. It fixes the problem, but it is a bad way to fix it. (BTW manually mounting drives does not change fstab)

---

### Post by kanikilu on 2009-03-09
For those NTFS partitions, does it change anything if you put "rw,user,auto" as the options rather than "defaults"?

BTW, text in quotes need a forward slash (/) to close.

---

### Post by 3Miro on 2009-03-09
Resolved:

the problem was in MountManager (I will find their web-page and post bug report or something). Here is what was happening:

MountManager running: cat /etc/fstab -> correct files with all UUID and partitions.
Apply changes and get out of MountManager: cat /etc/fstab -> reverts to / and swap only.

To solve the problem I had to make MountManager output the fstab file into another file and then sudo cp ***/fstab /etc/fstab. I cannot believe I did not try this before, probably because I did not think exiting MM would change fstab.

When I had manually set the file, I used /dev/sd** as opposed to UUID. That is probably the reason why it did not work that time.

Thank for all the help!

---

