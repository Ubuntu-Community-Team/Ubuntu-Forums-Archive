---
title: "Error: given UDI is a not a mountable volume (Flash Drive)"
date: 2005-10-17
forum: Desktop Environments
---

### Post by not_cool on 2005-10-17
I have a flash drive that has been able to automount the first week with Ubuntu Breezy Badger. After (at least I think so) I used the Synaptic Package Manager to get some packages, the drive wouldn't automount any more. I have tried mounting it via Nautilus but get Error: given UDI is not a mountable volume. I have tried to use the mount command but I am still confused on how to use it. Any suggestions?

---

### Post by Stormy Eyes on 2005-10-17
First, make a directory in which you can mount the drive with the following terminal command: 
```
mkdir /media/flashdrive
```
Once you've made the mount point, you can mount the drive with the following command:
```
sudo mount -t vfat /dev/sdaX /media/flashdrive
```
where /dev/sdaX is the location of your flash drive.

---

### Post by not_cool on 2005-10-18
Thanks. It solved my problem but I am still a little annoyed about it not automounting. Instead of having to type in the command each time, is it possible to to make a file that I can execute so I can mount the drive? The file would need sudo in it. Sorry for being such a noob. I just transfered over from a couple weeks on Fedora Core 4, my first try at linux. (I spend two weeks trying to install the kernel source, and about ten installs of the OS. Ubuntu is so much better! Go Synaptic Package Manager!)

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=not_cool]Thanks. It solved my problem but I am still a little annoyed about it not automounting. Instead of having to type in the command each time, is it possible to to make a file that I can execute so I can mount the drive? The file would need sudo in it. Sorry for being such a noob. I just transfered over from a couple weeks on Fedora Core 4, my first try at linux. (I spend two weeks trying to install the kernel source, and about ten installs of the OS. Ubuntu is so much better! Go Synaptic Package Manager!)[/QUOTE]

It's a bug in pmount-hal, and the problem also happens with floppies. It's being fixed.

---

### Post by not_cool on 2005-10-18
Thanks, I'm trying to use fstab right now which is nearly working, I just need to fix the mountpoint, which I know how to do.

---

### Post by not_cool on 2005-10-18
Do you know when the new updates are going to come out?

---

