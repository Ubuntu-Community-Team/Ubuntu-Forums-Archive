---
title: "Dual boot - add windows XP to Linux"
date: 2005-10-25
forum: Desktop Environments
---

### Post by mbailey on 2005-10-25
Could someone point me to a how-to on getting a dual boot system set up? Everything I have found so far assumes that you're trying to add Linux to an existing Windows setup. I need to go the other way, preferably without having to reinstall breezy after loading XP.

Thanks,
Martin

---

### Post by bullfrog on 2005-10-25
try going tohttp://www.linuxquestions.org/questions/answers.php?action=viewa... i found it there   good luck  bullfrog:razz:

---

### Post by mbailey on 2005-11-01
I'm getting closer. I now have XP loaded on one drive and breezy on the other and can boot each of them when the drive they're on is plugged into SATA 1. I think what I need to do next is leave XP on SATA1, install Grub in that drive and change the fstab on my breezy install so that it knows it's on SATA 2. 

Can I change the fstab while breezy is running and then close down & switch SATA cables, or do I need to boot under the live CD to make such modifications? I'm also unclear as to how to get Grub onto a disk which has nothing but windows on it. Any advice/abuse appreciated.

Thanks,
Martin

---

### Post by Pathogenix on 2005-11-01
You can change fstab whenever you feel like it. Modify it and reboot.

Is rebooting even necessary, anyone? Or if I were feeling brave, could I just umount -a && mount -a?

Getting grub into the boot partition of a drive containing Windows is no different to getting into the boot partition of a drive containing Linux. Just grub-install /dev/hda

I've got GRUB installed on both drives so that if one dies, I can boot from the GRUB console, but I'm famously paranoid and have no floppy drive.

You might want to get an emergency disk that can replace the windows boot loader in case of crisis.

[http://ebcd.pcministry.com/](http://ebcd.pcministry.com/) does the job nicely.

---

### Post by mbailey on 2005-12-07
Got it working finally. I found the trick from suggestions here: use GRUB to remap my two separate drives to fool windows into thinking it is on the primary; here's the entry in /boot/grub/menu.lst:

 ```

 title		Windows 95/98/NT/2000
 root		(hd1,0)
 makeactive
 map (hd0) (hd1)
 map (hd1) (hd0)
 chainloader	+1

```

Now ubuntu & windows can both boot to their respective hard drives. If only ubuntu could teach windows that the machine DOES have a network adapter. Oh well, some progress.

---

### Post by mbailey on 2005-12-12
Well, I thought it was working - Windows thought differently apparently. After patching, I could get the network adapter going. Both systems could boot, but windows crashed perpetually, mostly when opening IE. I removed the ubuntu drive from being primary & booted the windows drive in its place & now it is fine. It appears that something was not fooled by the GRUB drive mapping. Now I need to put grub on the windows drive so I can get to ubuntu on the second drive - any gotcha's there I should know about?

---

### Post by Tech_gogi on 2005-12-15
i was having the same problem, after i forked my drive... this is how i got it to work..> title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0) 
rootnoverify (hd1,0)
makeactive
chainloader	+1

just add [root (hd1,0)]("http://tinyurl.com/8zgfk") or where ever the xp side is located.

after that, add [rootnoverify (hd1,0)]("http://tinyurl.com/d4sdj") to get GRUB to kick the chainloader over, in turn kicking the Windows bootloader over..  hope this helps...

---

