---
title: "mount ntfs problem"
date: 2009-01-26
forum: General Help
---

### Post by belaviyo on 2009-01-26
Hi,

I use this code to auto mount my ntfs drive in /etc/fstab

/dev/sda1 /media/sda1 ntfs users,defaults,umask=000 0 0

Ubuntu usually mount a drive correctly but some times it doesn't do it so I must mount it manually from terminal using

mount /dev/sda1 /media/sda1 -o force


any body know what wrong with my fstab?

---

### Post by Joeb454 on 2009-01-26
I'm not quite sure why you're trying to use the force option when you mount the drive, other than you never shut down the NTFS drive correctly.

I like to think the link I have in my sig is a nice and easy way of auto-mounting NTFS drives. It's the method I use on my computers :)

---

### Post by belaviyo on 2009-01-26
I only use force option when auto mount doesn't work! (system start-up but ntfs drive doesn't mount)

My questions:
1. What is wrong with my fstab that cause this problem!

2. how to shut down the NTFS drive correctly ?

---

### Post by taurus on 2009-01-26
When you use windows, make sure you shut it down cleanly which means no hibernation or sleep mode crap.  And if you do that, Ubuntu shouldn't have any problem mounting it without using the force option.  But if you don't want to use the force option, you can fix it with ntfsfix.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo mount -a
df -h
```

---

