---
title: "Alternate installer's partitioner hangs at 50%"
date: 2008-12-22
forum: General Help
---

### Post by fiddler616 on 2008-12-22
I'm installing Xubuntu on an ancient laptop. So I burned the alternate installer CD, put it in, and started installing, going through the keyboard layout, region, computer name, etc.
However, the installer is hanging on the screen that says
> Starting up the partitioner
|_-----------_50%________|
Please wait. . .
I suspect the hard drive--part of it is corrupted, but Windows ME let me just pretend it was smaller, and didn't create any problems except for in ScanDisk and Norton Disk Doctor (or whatever the heck it's called)

Is there anything I can do about this?

Thank you.

---

### Post by japase on 2009-02-03
I have exactly the same problem. I’m trying to install Xubuntu 8.10 on an old laptop with 64 MB RAM using the alternate installer and command-line system installation option. The installation also hangs at 50% at the partitioner screen. But my hard drive is perfectly ok – I had XP on it and also tested to install DSL without any problems.

Any tips?

---

### Post by snowpine on 2009-02-03
I would not recommend xubuntu with only 64mb of ram. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) :

> Recommended minimum requirements

    * 300 MHz processor
    * 256 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 800x600 resolution 


DSL is a great choice for those specs.

---

### Post by japase on 2009-02-03
According to [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) (and some other articles and posts) Xubuntu works fine with 64MB.

The laptop I’m installing on is PIII MMX 266MHz, 4 GB HD and resolution 1024x768 (digital HiNote Ultra 2000).

I can live with DSL, but would like to test Xubuntu first (if possible, of course) before making the final choice.

Thanks!

---

### Post by snowpine on 2009-02-03
Sorry, I did not realize you were attempting a command-line only installation. Please disregard my last post. :)

---

### Post by snowpine on 2009-02-03
ps One suggestion is to pre-partition your hard drive (for example using the DSL live cd) prior to installing. That way, you can skip the partitioner step of the installation, which seems to be where you're getting stuck.

---

### Post by japase on 2009-02-03
Yes, that was also my first thought. That’s why I have installed DSL on the HD making two partitions: 192 MB for swap and the rest for root formatting as ext2. I could install DSL on HD without any problems. And run it, of course.

---

### Post by japase on 2009-03-03
Still didn’t resolve the problem… :(

But I came on an idea:
Could it be possible to move the hard drive to another lap-top, run the installation and swap it back directly after first shutdown?
Could it be a problem with another hardware/cpu on the second machine?

---

