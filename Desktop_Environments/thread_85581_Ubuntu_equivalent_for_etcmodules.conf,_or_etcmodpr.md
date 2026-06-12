---
title: "Ubuntu equivalent for /etc/modules.conf, or /etc/modprobe.conf ?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by jubei on 2005-11-03
Hi

I'm trying to increase my usb mouse polling rate to 500hz using this guide [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=62]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=62") But I have never configured module parameters before and I cant work out what file I'm supposed to edit since I don't have a /etc/modules.conf, or /etc/modprobe.conf file. If I create a /etc/modprobe.conf file and put the info in there it doesnt work. I have successfully achieved the 500hz by editing /sys/module/usbhid/parameters/mousepoll so I know my system is capable.

How can I make it so the module is configured for 500hz (2ms) when I boot up?

Thanks in advance for the help.

Jubei

---

### Post by bionnaki on 2005-11-03
sudo gedit /etc/modules

---

### Post by jubei on 2005-11-03
[QUOTE=bionnaki]sudo gedit /etc/modules[/QUOTE]

Thanks, I added the line

```
options usbhid mousepoll=2
```

to /etc/modules

This didn't achieve the desired effect. Are you sure this is the right file. If so what else could be going wrong?

---

### Post by slux on 2005-11-03
/etc/modules is for loading modules automatically at startup, a useful feature but probably not what you're looking for..

I believe you can create new file listing your desired options in /etc/modprobe.d

I seem to recall there used to be an actual modules.conf in Debian-based distros as well... Guess that has been phased out in favor of just modprobe.d

---

### Post by jubei on 2005-11-03
[QUOTE=slux]
I believe you can create new file listing your desired options in /etc/modprobe.d
[/QUOTE]

Thanks for the info slux. I created a file called /etc/modprobe.d/usbhid.modprobe and put the option in that file. I then rebooted and my usb polling rate was still the default :confused:. Does this mean I have to use the kernel parameter method? If so how do I "Pass module parameters to drivers that are built directly into the kernel" in breezy?

---

