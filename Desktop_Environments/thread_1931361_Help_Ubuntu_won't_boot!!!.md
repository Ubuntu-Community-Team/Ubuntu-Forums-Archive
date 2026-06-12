---
title: "Help Ubuntu won't boot!!!"
date: 2012-02-25
forum: Desktop Environments
---

### Post by TheNadeWhisperer on 2012-02-25
Hi guys, I'm dualbooting win7 an Ubuntu 11.10. Sometimes Ubuntu will boot good, and I can use it etc. sometimes it drops to busybox . It'll load grub, ask Ubuntu or win7 then when I hit Ubuntu it either goes to a purple screen(normal) or black with blinking white cursor. On the black screen after  a minute I get this code-
BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs)

Could somebody possibly help me out?? Thank you!

---

### Post by namdude0373 on 2012-02-25
Before it does it say ```
Gave up waiting for root device.
```or something like that?

---

### Post by TheNadeWhisperer on 2012-02-25
No it just blink at the whte cursor and then goes straight to the code I wrote.

---

### Post by oldfred on 2012-02-25
From grub menu press e and remove quiet & splash. Then you can see the boot process and try to catch where it is hanging up.

You can also see what was the previous boot processes with the log file viewer and just look for a process that takes a very long time or repeats in trying to run something.

Intermittent is the worst to resolve as you are not getting the same error every time.

Related to namdude0373's post sometimes a fsck may help and cannot hurt.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by TheNadeWhisperer on 2012-02-25
Sorry, I don't get the part changing the sdb1 to partition?? Would I use gparted?

---

### Post by oldfred on 2012-02-25
No just in the command I use the example of sdb1, you just use your partition whether sda1 or sda5 or each one separately. I used to use sdXY where X was drive and Y was partition and many thought they were supposed to use X & Y not a for X and 5 or Y as another example for sda5.

If you do not know your ext formated partition numbers run this.

sudo fdisk -lu

Then for every partition with ext3 or ext4 run the e2fsck command.

---

### Post by pawanthegunner on 2012-04-27
I have the same problem. running e2fsck returns error, so i run it forced and ignore error. it says file system was modified. what to do next?

---

### Post by oldfred on 2012-04-27
@pawanthegunner
May be best to create own thread. 

You did run it from liveCD not from working system as that can cause more damage than it fixes, if partition is mounted and trying to use the data as fsck is rewriting it.

---

