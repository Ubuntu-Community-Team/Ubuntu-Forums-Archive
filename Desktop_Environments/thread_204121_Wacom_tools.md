---
title: "Wacom tools"
date: 2006-06-26
forum: Desktop Environments
---

### Post by johnvand on 2006-06-26
I have finally jumped off the Microsoft wagon and landed headlong into the Linux world and I now know how little I know about computers in general.

I need some help !! ( Please )

I installed and edited the Wacom drivers for my Graphire tablet and got it working perfectly.  I also installed, I thought, the tools program but try as I might I can't find where these tools are.  Does anyone know?

Also, I have a Samsung CLP500N setup on my router as 192.168.1.116.  I downloaded the driver from Samsung themselves and when I click on the setup file nothing happens - I need more help !! :( 

I would appreciate anything you could do for me.

Thanks in advance,

John

---

### Post by twisted_steel on 2006-06-26
Welcome to Ubuntu :-D

The Wacom package installs a few debugging programs and some udev rules that make it easy to find out which device on your system is the tablet.  To see everything installed by the package, you can open up Synaptic Package Manager (in the System -> Administration menu).  Search for wacom and you will see wacom-tools listed.  Right-click on that entry and go to Properties.  You should see a window giving you an overview of the package; the Installed Files tab lists everything installed by the package.  The programs you can run are listed under /usr/bin - so in this case, they are wacdump, xidump, and xsetwacom.  You can read more about the tools by opening up a terminal and typing, for example ```
man wacdump
```

---

### Post by johnvand on 2006-06-27
Thank you very much - I do appreciate the help

---

