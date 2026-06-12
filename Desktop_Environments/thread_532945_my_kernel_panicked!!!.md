---
title: "my kernel panicked!!!"
date: 2007-08-23
forum: Desktop Environments
---

### Post by pinoyskull on 2007-08-23
need help guys, my Ubuntu died, it freezes on the splash screen and my keyboard indicators is blinking, i rebooted to recovery mode and found myself on a kernel panic page, here's a snippet 

---
[   3.866250] EIP: [<e0987b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:c14a5ce0
[   3.866383]    <0>Kernel panic - not syncing: Attempted to kill init!
[   3.866474] 
---

before it happened, i enabled ntfs-3g on fstab cuz I got a winxp installed too, after a few reboots (i was setting up some softwares in winxp that time) then that happened.

need help guys.

---

### Post by wieman01 on 2007-08-23
You are in trouble... ;-)

Can you undo the changes in 'fstab' by loading the Live CD and mounting the root file system?

---

### Post by pinoyskull on 2007-08-23
big trouble indeed, i edited my fstab and commented out the mount for ntfs drive, still the same banana :(

---

### Post by wieman01 on 2007-08-23
> **pinoyskull said:**
> big trouble indeed, i edited my fstab and commented out the mount for ntfs drive, still the same banana :(
Then you do have a problem. I'll shut up.

---

### Post by pinoyskull on 2007-08-23
i hope there's a solution, i don't want to reinstall everything :(

---

### Post by gmaniac on 2007-08-23
Ok, this is like shooting in the dark but that [ext3] showing there could mean something... You could try from a live cd

fsck.ext3 -fc/dev/ [root partition]

root partition the partion of your linux install 
i.e
```
fsck.ext3 -fc/dev/hda1
```

I never heard of ext3 oops (it's considered extremly stable) so either
somehow you have a really corrupted filesystem or there is some problem
with your hardware (check memory, cpu heat etc more probable causes) 

One other longshot  you could try is chrooting to your installation and trying re-installing the kernel packages after an apt update .... 
Read here [http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

I'm really quite curious as to what you find/do..
Best of luck.

---

### Post by pinoyskull on 2007-08-23
**gmaniac**

i did run fsck and filesystem's fine with the check

your other suggestion could be a possible fix but im still waiting for others to reply, maybe there's an easier or safer way to do it.

here are some screenshots i took from my nokia fone for reference
[http://i20.photobucket.com/albums/b2...8232007003.jpg]("http://i20.photobucket.com/albums/b230/pinoyskull/08232007003.jpg")
[http://i20.photobucket.com/albums/b2...8232007002.jpg]("http://i20.photobucket.com/albums/b230/pinoyskull/08232007002.jpg")
[http://i20.photobucket.com/albums/b2...8232007001.jpg]("http://i20.photobucket.com/albums/b230/pinoyskull/08232007001.jpg")
[http://i20.photobucket.com/albums/b2...l/08232007.jpg]("http://i20.photobucket.com/albums/b230/pinoyskull/08232007.jpg")

---

### Post by luvr on 2007-08-23
> **pinoyskull said:**
> my Ubuntu died, it freezes on the splash screen and my keyboard indicators is blinking
Don't know if your situation is in any way similar to mine, but my Dell Latitude D820 laptop does that every now and then on cold boot (i.e., first boot after power-on). In my experience, I can avoid the problem if I first boot from a Live CD (I use [SystemRescueCD,]("http://www.sysresccd.org") but any Linux Live CD should do, really), and run the following command:
```
fdisk -f /dev/*<partition>*
```
The *fdisk* won't find anything wrong, but if I subsequently reboot *(but from hard disk this time),* the system will start up just fine. Looks to me like there's one or another component going out of spec on cold boot, and the *fdisk* is the kind of warming-up exercise that it needs.

---

