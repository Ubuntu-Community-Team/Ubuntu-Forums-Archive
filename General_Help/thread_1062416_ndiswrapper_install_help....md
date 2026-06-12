---
title: "ndiswrapper install help..."
date: 2009-02-06
forum: General Help
---

### Post by jnd426 on 2009-02-06
Sorry if this is a stupid question but I am new to Ubuntu. I need to install ndiswrapper to install drivers for my wireless card. The problem is that every how to that I have found you need the install disk in the cdrom drive and I installed Ubuntu 8.10 from a flash drive. Help please....Thanks.

---

### Post by 2hot6ft2 on 2009-02-06
Should be here
System>Administration>Windows Wireless Drivers
if not open a terminal
Applications>Accessories>Terminal
and use
```
sudo apt-get install ndisgtk
```
then it will be there.

Naturally you'll need an internet connection to download it.

---

### Post by jnd426 on 2009-02-06
Oh sorry thats the problem I need to install the drivers for my wireless card to get internet connection.

---

### Post by mb_webguy on 2009-02-06
I don't know what HowTos you've been reading, but I have no idea why they'd tell you that you need the cd.  You do, however, need to be connected to the internet, so grab a cable and plug in.

What you do need is the Windows wireless driver.  You can download this from several locations on the Internet.  If you have an HP or a Dell you can download the driver from the appropriate website.  You'll probably find it as an exe file (which is actually a self-extracting zip archive).  Just use Archive Manager to extract it.  Inside somewhere should be an inf file, which is the actual driver.

The easy way to use ndiswrapper is with the ndisgtk gui.  In the terminal, type "sudo apt-get install ndisgtk".  This will give you a Windows Wireless Drivers option in the System->Administration menu.  Open this, click Install New Driver, and locate the inf file to install the driver.

You now may or may not be able to use Wi-fi.  If not, follow the [ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847") on the networking forum.

---

### Post by 2hot6ft2 on 2009-02-06
> **jnd426 said:**
> Oh sorry thats the problem I need to install the drivers for my wireless card to get internet connection.
Ok, do you have another linux box with internet access? Or windows? How do plan on downloading it?

---

