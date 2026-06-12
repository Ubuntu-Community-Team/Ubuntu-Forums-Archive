---
title: "Ubuntu won't boot up after updates"
date: 2009-04-24
forum: General Help
---

### Post by calvinps on 2009-04-24
Hello.
 
Last night I was installing some updates, but I only had time to install some of them because my parents take my laptop away during the night.
 
When I restarted my computer, the splash screen just stayed there for a minute, then some text appears, and it says:
 
ALERT! Root filesystem (...) does not exist. Dropping back to a shell...
 
and the initramfs prompt comes up.
 
I would hate to reinstall Ubuntu but if that's the case, looks like I would have to.

---

### Post by Peter09 on 2009-04-24
You may be able to rescue this using the LiveCD. I believe it has the capability to rescue a faulty system. 

I am unsure whether this is only for the Alternate CD or the LIVE CD will do it as well. Its worth a little googling to find out.

---

### Post by calvinps on 2009-04-24
How do I repair the system using the Live CD?

---

### Post by Peter09 on 2009-04-24
I believe with the AlternateCD there is an option to 'Rescue the system' when you boot from the CD.

---

### Post by jamessnell on 2009-04-24
Can you post your /boot/grub/menu.lst file?

```
cat /boot/grub/menu.lst
```

I suspect your kernel/boot setup didn't make it.. Sounds sort of like a problem I had due to no initrd being provided..

---

### Post by calvinps on 2009-04-24
I can't access it.
 
Like I said in the first post, Ubuntu is unable to mount the root filesystem.
 
Any more ideas? (specifically regarding to repairing via the Live CD)

---

### Post by jamessnell on 2009-04-24
> **calvinps said:**
> I can't access it.
 
Like I said in the first post, Ubuntu is unable to mount the root filesystem.
 
Any more ideas? (specifically regarding to repairing via the Live CD)

Sure, but you should be able to mount it if you boot off the LiveCD, mount the file system and look around...

---

### Post by calvinps on 2009-04-24
Cool
 
How do I mount it using the LiveCD?

---

### Post by jamessnell on 2009-04-24
> **calvinps said:**
> Cool
 
How do I mount it using the LiveCD?

Open a terminal and type something like:
```
sudo mount /dev/sda1 /mnt
```

In order to figure out what partition/drive to mount, try using something like this: ```
sudo fdisk -l /dev/sda
```

You can try other drives such as "sdb", "sdc", etc.. Maybe "hda"..

That may help..

---

### Post by calvinps on 2009-04-24
> **jamessnell said:**
> Can you post your /boot/grub/menu.lst file?
 
```
cat /boot/grub/menu.lst
```
 
I suspect your kernel/boot setup didn't make it.. Sounds sort of like a problem I had due to no initrd being provided..
 
Still can't access it - its saying that the file doesnt exist :confused::confused::confused:
 
Any more solutions? Try to stick to repairing off the LiveCD

---

### Post by jamessnell on 2009-04-24
Is a fresh install an option?

You can use gparted to survey the drives attached to the system from the LiveCD

---

