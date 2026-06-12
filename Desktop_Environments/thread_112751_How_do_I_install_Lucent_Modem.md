---
title: "How do I install Lucent Modem?"
date: 2006-01-05
forum: Desktop Environments
---

### Post by 123hamster on 2006-01-05
I just installed ubuntu on my desktop and I am not sure how I can install my Lucent winmodem.  I went to check the device management and it seems to recongize my modem.  However as I was trying to set up my connection it would not detect the port.  I was reading something about adding a line of rules into /etc/udev/roots.d but it refuse to let me save the 10-local.rules.  I am not even sure if that is the right steps to take.  If anyone can help me out it would be apperciated.

---

### Post by FizDev on 2006-01-05
Hi,
First of all when you want to edit the roots.d be sure to put the "sudo" before your command. Also I do not know for Ubuntu, but I had been able to make work my Lucent Modem in Gentoo utilising  the drivers found at this adress :[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem) Just follow the directions and you should be able to work it out. ;)

Also, you might want to search in this forum for "Lucent Modem" if you haven't already. You should find what you are looking for.

Note : I've just seen these, might help you out!
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29)
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)
[https://wiki.ubuntu.com/SmartLinkModemDriverHowTo/FromSource?highlight=%28modem%29](https://wiki.ubuntu.com/SmartLinkModemDriverHowTo/FromSource?highlight=%28modem%29)

---

### Post by hajk on 2006-01-05
You can download the Debian "ltmodem" package for your kernel version from
[http://linmodems.technion.ac.il/packages](http://linmodems.technion.ac.il/packages), then install it with 

sudo dpkg -i <package-name>.deb

This provides the modules "ltserial" and "ltmodem" that should be loaded automatically on boot. The first time, you can load them manually with 

sudo modprobe ltserial

Check with "cat /proc/modules" whether this was successful.

No need to start messing around with udev, the device /dev/ttyLTM0 will already have been made, linked to /dev/modem.

---

