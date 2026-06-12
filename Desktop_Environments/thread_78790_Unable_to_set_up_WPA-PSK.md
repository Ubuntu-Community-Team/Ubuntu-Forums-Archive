---
title: "Unable to set up WPA-PSK"
date: 2005-10-18
forum: Desktop Environments
---

### Post by dizbah on 2005-10-18
I got my Dell Inspiron 6000 to recognize both my wireless cars but can't connect.  The lights are both lit but in order for me to connect to my router I need the WPA option to set but get the following error.....


dell@laptop:/etc/ndiswrapper/bcmwl5$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wpasupplicant


I am unable to install.  Please help.

---

### Post by lonetree on 2005-10-24
I can install the wpa_supplicant successfully, but I got problem with the auto startup. 

For your case, did you set your repositories correctly?

Good Luck.

If you are able to get it work, send me a note.

Search around, there are quite a fair bit of thread discussing about this, including the steps in installation. But to get it really work, it kinda difficult. Wonder why linux is not as easy in installing things.

:-)

---

### Post by YanH on 2005-10-24
> But to get it really work, it kinda difficult. Wonder why linux is not as easy in installing things

Unfortunately this is because many Manufacturers do not provide any driver support for their devices in Linux. When you install a new device in windows it works because the Manufacturer provides a CD which tells windoze how to deal with it, if it wasn't for this it wouldn't work. 

Most of the wireless cards that work in Linux work because people have written their own driver in the absence of the Manufacturers. This also means that all of the extended features may not work.

Slowly more manufacturers are providing supports for Linux ( Printers, Graphics Cards etc ) but unfortunately for things like Wireless technology this doesn't seem to be happening too widely yet. The best thing you can do to improve this situation is to complain to the manufacturer, and ask them why there isn't a Linux Driver for the device you've just bought. If enough of us keep complaining then it might help persuade them to produce drivers for Linux as well.

---

### Post by krake on 2005-10-24
Hi dizbah,

the wpasupplicant package is in the universe repository so you'll need to have that in your sources.list file to be able to install it.

---

