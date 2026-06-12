---
title: "X is broken after attempted reinstall of nvidia drivers"
date: 2007-02-22
forum: Desktop Environments
---

### Post by band-aid on 2007-02-22
I compiled a new kernel a few nights ago and therefore needed to reinstall my Nvidia drivers. Well I have so far only managed to break my drivers when booting under my old kernel. I normally use automatix so I am not used to installing them manually. Currently I am only able to boot using the recovery mode. With any of my kernels it tells me that X has failed and leaves me at a blinking cursor. How can I get my GUI back?

---

### Post by statictonic on 2007-02-22
You can go back to the default drivers if you need the GUI to find new drivers or what not.

First make a backup copy of /etc/X11/xorg.conf then edit /etc/X11/xorg.conf  using nano or vim

IE
vi /etc/X11/xorg.conf/
or
nano /etc/X11/xorg.conf 

Look for the driver section like below.  Change nvidia to nv and save.  

Section "Device"
    Identifier     "NVIDIA Corporation"
    Driver         "nvidia"


Then type /etc/init.d/gdm restart
If that doesn't work just reboot.

---

### Post by hscottyh on 2007-02-22
I'm curious, why did you need to compile a new kernel?

---

### Post by MasterOfDisaster on 2007-02-22
You might have to install the nvidia drivers manually, as only the standard Ubuntu kernels are supported for the driver from Automatix.

---

### Post by kdawg on 2007-02-23
I just recently compiled the 2.6.20 kernel and had to reinstall the nvidia drivers... I followed this tutorial and it worked perfectly!

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

I used Method 2 because I compiled my own kernel from source.

---

