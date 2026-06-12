---
title: "Creating a Windows Boot Disk with a Linux Machine"
date: 2008-09-27
forum: Desktop Environments
---

### Post by sendaletterbomb on 2008-09-27
I need to create a Windows boot disk for a PC that is currently melting down. I found the .exe I need, but the only computer that I have with a floppy disk drive is my Ubuntu Hardy machine. Can I create a Windows boot disk using this machine?

---

### Post by howefield on 2008-09-27
Hardy won't know how to handle the .exe, you'll likely need Wine installed to make your floppy.

---

### Post by sendaletterbomb on 2008-09-27
I don't need to execute the file on Ubuntu, just make the floppy. On Windows, when formatting a disk, there is an option labeled "Create an MS-DOS Startup Disk." Is this possible to do with Hardy?

---

### Post by howefield on 2008-09-27
sorry, I assumed that your exe file was a self extracting file which formats and writes the windows startup disk.

Go to Places, then Computer. You will see the floppy drive, right click on it and choose Format. Don't know if it includes startup functions or options, but one way to find out ;)

(I don't have a floppy drive on this machine or I'd try it)

---

### Post by lykwydchykyn on 2008-09-27
To create a bootable DOS disk, you'll probably need to acquire a disk image of DOS and use dd to put it on a floppy.  I don't know if for your application FreeDOS would work, but you can get a boot disk image based on FreeDOS here:
[http://www.finnix.org/Balder](http://www.finnix.org/Balder)
Download that file, and make a disk with it using this command:
dd if=Balder10.img of=/dev/fd0

---

