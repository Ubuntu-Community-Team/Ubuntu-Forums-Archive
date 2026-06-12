---
title: "dual boot: runing linux with a VM on winXP"
date: 2007-09-02
forum: Desktop Environments
---

### Post by tom_a_sparks on 2007-09-02
I have setup my computer with both winXP and ubuntu (dual boot)
I would like to use a VM to run ubuntu on windows for i can have some internet access in ubuntu
and for I dont have to reboot back and forward to download stuff

---

### Post by Fonon on 2007-09-02
first, download Virtual Box for windows. [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Then download the Ubuntu .iso image.  It's found at [www.ubuntu.com](www.ubuntu.com)

Hit new Virtual Machine, pick Linux as the VM type, and then go through the process.  After your done, go into the properties of the machine, and set the 'mount CD Drive" to yes, and go to your iso image of Ubuntu.  Be sure to set the option to "ISO image".

If I explained everything right, you should be able to have a VM of Ubuntu!

---

### Post by tom_a_sparks on 2007-09-02
I have ubuntu all ready setup up on other partition on my hard drive

---

### Post by Fonon on 2007-09-02
> **tom_a_sparks said:**
> I have ubuntu all ready setup up on other partition on my hard drive

I know.  You requested to create a VM for Ubuntu to use for Windows, and I just told you how.

---

### Post by tom_a_sparks on 2007-09-02
this was what I was looking for
> qemu.exe -L . -m 128 -soundhw all -localtime -hda \\.\PhysicalDrive0 -snapshot

---

