---
title: "Select OS screen help"
date: 2009-04-24
forum: General Help
---

### Post by Unkuiri on 2009-04-24
Hi, I've installed my Ubuntu OS on a external usb hard drive (I have a Windows XP OS on my computer's hard drive) and it starts the bootloader from that external device and when I start the computer if I doesn't have the external drive plugged in it's impossible to enter even in windows...Is there a way to install the bootloader to the disk where the windows OS is installed or other way that let me enter windows without having to have the external hard drive plugged in?

Thanks in advance

---

### Post by Kareeser on 2009-04-24
Take a gander through this thread :)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Unkuiri on 2009-04-24
Thanks for the answer...I've tried what you pointed but still getting an error 21 when I try to initialize without the external disk plugged in...:(..and when I do again the find operation in grub mode it shows that the operation that i've just made was useless, it shows grub was yet installed in the same (external disk's) partition...Can you halp me then?

---

### Post by Kareeser on 2009-04-24
Right... as you correctly diagnosed, your GRUB is installed on your external hard drive. The solution is to use a Live CD and drop into the recovery console, in order to reinstall GRUB onto the resident hard drive.

The link I pointed to above should help you out.

---

