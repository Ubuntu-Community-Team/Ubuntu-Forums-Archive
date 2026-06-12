---
title: "Ubuntu Jaunty and ATi 4XXX"
date: 2009-04-24
forum: General Help
---

### Post by Legace on 2009-04-24
Hello guys.

I am currently using the open source ATi driver, without problems, but I can't enable Compiz.

I tried the FGLRX driver 3 times, and had to reinstall Ubuntu (3 times) to get the machine to work.

If I enable FGLRX, the screen will be black and have red/green dots and lines everywhere.

Any idea when 3D acceleration will be available for the open source drivers for the Radeon 4XXX series?
Or any clue on how to get FGLRX working properly?

Thanks.

---

### Post by Legace on 2009-04-25
Up.

---

### Post by gocek on 2009-04-25
Hi

I'm currently on HD4870 with Ubuntu 9.04. I have installed newest drivers (Catalyst 9.4 ver. 8.602) from ATI's website. And they work... sometimes. Yesterday I booted up after installation and everything was ok. Two hours later, the system would hang after typing in password, showing only black screen. And I didn't change anything ... And today it works again, no changes made either...

If you want to try this path, go here:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP. 

Report back if you have any questions ;)

BTW: if you fail to boot up your Ubuntu, just reboot it, select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

