---
title: "how to allocate swap space ??"
date: 2009-06-11
forum: General Help
---

### Post by kushal.7 on 2009-06-11
I installed ubuntu manually.
I didn't allocate the swap space at that time. Is there any way to allocate the swap space now ??... 
1 gb ram, ubuntu 9.04

---

### Post by Therion on 2009-06-11
You'll need to boot to a gParted LiveCD, shrink an existing partition and create a swap partition in the newly created free-space.  

Post back if you need detailed instructions.

---

### Post by synapsys on 2009-06-11
Glad to hear you got it installed. Open up gparted and make a swap partition 1.5x the size of your ram. Take note of the location e.g... /dev/name

Then open up terminal and type:

```
sudo swapon /dev/name
```

---

### Post by kushal.7 on 2009-06-11
> **Therion said:**
> You'll need to boot to a gParted LiveCD, shrink an existing partition and create a swap partition in the newly created free-space.  

Post back if you need detailed instructions.

ya tell me in detail... i dont understand

---

### Post by bodhi.zazen on 2009-06-11
If you do not wish to resize your partitions and make a swap partition you can make a swap file.

[http://www.go2linux.org/Swap-memory-increase-with-swap-file](http://www.go2linux.org/Swap-memory-increase-with-swap-file)

---

### Post by kushal.7 on 2009-06-11
thank you all,

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
this helps me a lot

what is gparted live cd ??

---

### Post by kushal.7 on 2009-06-11
swap space sucessfully allocated, but its still not hibernating...

---

### Post by LKjell on 2009-06-11
> **kushal.7 said:**
> thank you all,

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
this helps me a lot

what is gparted live cd ??
You can use your Ubuntu live cd. However if your filesystem you want to resize is ext4 then you need to use the latest live cd (9.04) since that one has support for ext4 filesystem. Other than that it is possible to install gparted and do an online resize if you use ext3. You can check which filesystem you are using by going to System => System Monitor => Filesystem. Note the filesystem there are taken from /etc/fstab file so you might have ext4 if you manually upgrade from ext3 but forgot to change the fstab file. So to check which feature your filesystem has you might want to do a dumpe2fs -h command to check. The command requires you to use sudo. Example:

sudo dumpe2fs -h /dev/sda1

---

