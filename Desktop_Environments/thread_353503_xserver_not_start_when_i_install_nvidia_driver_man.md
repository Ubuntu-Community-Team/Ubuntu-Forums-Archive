---
title: "xserver not start when i install nvidia driver manual"
date: 2007-02-04
forum: Desktop Environments
---

### Post by nemanaldin on 2007-02-04
hi 
i download and install nvidia driver and then i cant login to ubuntu graphically and it say that xserver have a problem
[http://i18.tinypic.com/2l900zm.jpg](http://i18.tinypic.com/2l900zm.jpg)
and when i type startx it say
[http://i19.tinypic.com/4bhnzhf.jpg](http://i19.tinypic.com/4bhnzhf.jpg)
my ubuntu 6.06 and fx5200 graphic card
plz help me

---

### Post by dcstar on 2007-02-04
> **nemanaldin said:**
> hi 
i download and install nvidia driver and then i cant login to ubuntu graphically and it say that xserver have a problem
[http://i18.tinypic.com/2l900zm.jpg](http://i18.tinypic.com/2l900zm.jpg)
and when i type startx it say
[http://i19.tinypic.com/4bhnzhf.jpg](http://i19.tinypic.com/4bhnzhf.jpg)
my ubuntu 6.06 and fx5200 graphic card
plz help me

Ok, you have to have the correct Nvidia package installed for your kernel (and card).

Firstly, do CTRL-ALT-F1 and log into a terminal screen, then:
```
sudo nano /etc/X11/xorg.conf
``` and change the "nvidia" driver string to "vesa", exit and save the file.

Then do:
```
sudo /etc/init.d/gdm restart
```
and you should get a basic X system to work with.

Now go into Synaptic, do a search for "Nvidia" and install either the legacy driver or the other one (it depends on how old your card is as to which one is required).

Once you have an install done, you can again edit your /etc/X11/xorg.conf file and put the nvidia back in - then CTRL-BACKSPACE to restart your X system to see if it works!

If it doesn't, you can repeat the process and try another choice.

---

### Post by rykel on 2007-02-05
Hi,

I am able to get NVIDIA 9746 driver up and running properly with GeForce Go 6600 on my Toshiba M40 laptop.

However, whenever I reboot, I have to reinstall the driver.

I have tried using "sudo dpkg-reconfigure xserver-xorg" (to set the driver to "nvidia") and the xconfig program in the driver itself, but neither could retain the use of the driver upon a reboot.

Anyone advice here?   :confused:

---

### Post by Freaky_Llama on 2007-02-05
Hello. I had this issue an hour ago while installing the driver for my 7900GS on 6.10

This is what I had to do to restore xserver to working:

Go into your backup copy of xorg.conf (nvidia installer saves it as /etc/X11/xorg.conf.backup)

use your fav editor to look at that file. Look for the line "BusID" in the Video Card section. Mine for PCI-e was: ' BusID "PCI:5:0:0" '

Write or copy the line down.

Edit the new xorg.conf and place that line in the same place it was in the backup conf.

Also, I removed the section that mentioned "DRI" which was at the bottom.

Now I'm :guitar:  with Beryl :)

---

