---
title: "Virtualbox - Virtual disks and Virtual Machines"
date: 2008-12-07
forum: Desktop Environments
---

### Post by ThatOtherGuy on 2008-12-07
Hi there,

This question is probably more suited in a Virtualbox forum, but I find you guys way more helpful and informed.

I have Virtualbox running on Ubuntu 8.04. I created a WinXP(urggg!!!) virtual machine and everything was going well. I did what I wanted to do and then I got a message saying that the (virtual)drive was full. So, in my infinite wisdom, I deleted the virtual drive but not the virtual machine. I figured I would create a new, larger virtual drive, load my virtual machine in it, and be ready to go on working.

For some reason, I could not get my VM to boot from the VHDD I created. Where am I going wrong? Is it my lack in understanding of the VM vs VHDD? Have I lost all my work when I deleted the virtual drive?

Thanks!

---

### Post by albinootje on 2008-12-07
Did you delete the virtual disk with the disk-manager in VirtualBox ?
Or did you detach it ?
Check your ~/.VirtualBox/ directory for .vdi (virtual hdd) files.

---

### Post by the yawner on 2008-12-07
The way I understand it, the virtual machine is equivalent to an actual PC... minus the HDD. The HDD where you actually install your operating system and store all data is the virtual disk. So when you replaced your virtual disks it's like having a brand new HDD with no OS.

That said, I hope you haven't deleted the .vdi file.

---

### Post by ThatOtherGuy on 2008-12-07
Hi. I checked in the folder you suggested, and the file was there. Obviously i must have just deleted it in the app itself. So i'm glad to say i never lost anything. Thanks for all the advice. I was under the impression everything was in the vm. So if the os and allyour files are in the virtual disk, whats the point of having a dynamically expanding image file? The image file shouldn't increase much after it's set up, would it?       Thanks!

---

### Post by the yawner on 2008-12-08
If you've set a virtual disk to a dynamically expanding image, the size of the vdi file will only increase as you save more data on your virtual machine/disk, until it reaches your defined image size. Hence you still need to anticipate how much disk space you'd allocate for your virtual machine.

---

