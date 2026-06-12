---
title: "usplash weirdness after restoring backup"
date: 2009-01-16
forum: General Help
---

### Post by kano on 2009-01-16
Hi,

I just recently had to backup the girlfriends laptop running 8.10, so that I could repartition and install vista alongside ubuntu. (she needs it for a class this semester) I backed up her root partition onto my file server using tar (preserve permissions, etc), repartitioned, installed vista and restored the tar archive. 

After changing the new UUIDs into grub and fstab, everything is working fine... except usplash on boot. It will do the bouncing back and forth bar thing, then go into text mode where it should start doing the progress. Shutdown shows usplash fine. 

I've tried regenerating the initramfs using startupmanager, but it doesnt seem to do anything. I'm not sure where else to look to fix this, as I'm not familar with ubuntu's startup scripts. (I run archlinux myself)

thanks :KS

---

### Post by dcstar on 2009-01-16
> **kano said:**
> 
........
After changing the new UUIDs into grub and fstab, everything is working fine... except usplash on boot. It will do the bouncing back and forth bar thing, then go into text mode where it should start doing the progress. Shutdown shows usplash fine. 

I've tried regenerating the initramfs using startupmanager, but it doesnt seem to do anything. I'm not sure where else to look to fix this, as I'm not familar with ubuntu's startup scripts. (I run archlinux myself)


```
sudo update-initramfs -k all
```

---

### Post by MaindotC on 2009-01-16
Hey how about if you just run Vista in a VM?

---

### Post by lavinog on 2009-01-17
what if you change the ubuntu entry in grub to replace "quiet splash" to "verbose" (no quotes)
And see if it says anything odd.

---

### Post by kano on 2009-01-23
> **dcstar said:**
> ```
sudo update-initramfs -k all
```
Not valid, but I tried `update-initramfs -ck all` and it did nothing.

> **strAlan said:**
> Hey how about if you just run Vista in a VM?
The only copy of vista I have locks up when trying to boot inside of a VM. That, and I worry about the performance hit of running it in a VM. If it sucks so much running it for real, what's a VM gonna be like? :p

> **lavinog said:**
> what if you change the ubuntu entry in grub to replace "quiet splash" to "verbose" (no quotes)
And see if it says anything odd.

I will give that a try and report back.

edit: No errors, everything looks fine.

---

