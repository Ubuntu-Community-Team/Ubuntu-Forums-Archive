---
title: "XP in VirtualBox"
date: 2009-07-08
forum: Desktop Environments
---

### Post by sharathpaps on 2009-07-08
Hey,
       I managed to setup XP within VirtualBox in Ubuntu 8.10. Just have a few doubts regarding that now:

1. Do I need to use an antivirus for this XP installation?

2. Can I go ahead and install programs as usual?

3. Will this installation of XP require updates and stuff?

4. Will I be able to access files in my /home partition from XP?

Thanks...

---

### Post by l33t_3lv3n_g33k on 2009-07-08
For Questions 1, 2, and 3 the answer is YES!  Take care of the virtual machine exactly as you would a Windows machine.  
 
As for accessing your /home directory, that depends.  There are ways to set it up so that you should be able to access your linux partitions.  The easiest method would be to establish a "shared" partition that is FAT32 or NTSF.

---

### Post by pmlxuser on 2009-07-08
You will be running xp in virtual system (operating system running in a file /folder) accessing files in your home directory i think is not possible.

you can install programs as you do in windows

windows will require update as usual for windows

An antivirus will be required in the virtual system - you don't want to have an infected virtual OS. However there are no risks of the virtual OS infecting your actual systems if that is your fear.

And yeah you might be required here and there to install dirivers in your virual machine OS

---

### Post by sharathpaps on 2009-07-08
Hi, Thanks for your help. I've installed an antivirus and have updated XP. I even managed to share a folder between Ubuntu and XP. Now I have another problem.. The guest OS can only be used inside a window. Activating seamless mode seems to crash the whole thing. I think installing drivers for my GeForce MX4000 might help but can I insall drivers even while ubuntu is using the same piece of harware? Will there be any conflict?

---

### Post by l33t_3lv3n_g33k on 2009-07-08
Been a while since I've used VirtualBox, but if my memory serves correctly then the "Video card" used by the virtual machine is a generic one (could be confusing that with VMWare...).

You can download and install the windows version of the driver for your video card provided the virtual machine is recognizing it as your GeForce MX4000.  It won't cause any conflicts, but possibly a reduction in performance since Ubuntu is between the hardware and the virtual machine.

---

### Post by nerdy_kid on 2009-07-08
just share a folder in VBox and create a link to / and stick it in the folder.  That will work.

---

