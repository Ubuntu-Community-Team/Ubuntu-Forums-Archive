---
title: "Booting into low graphics mode after install aticonfig"
date: 2009-05-27
forum: General Help
---

### Post by johnhdsi on 2009-05-27
I have 8.1 installed on my box and it has been running perfect. I finally got all of my graphics woes taken care of except an occasional hang when I run Steam client under Wine. I did aticonfig and it told me that I didn't have it installed and gave me the code to install it (I was using the CLI). So I ran the install and it downloaded and installed alot of files. Everything has been working fine until I rebooted the machine. It boots into low graphics mode and I cannot get it out of this mode. I tried the recovery through grub, I also tried to create a new config but the box just sits there. I decide to go with the create new option but I am having the same problem. Is there any way to roll back what I did? I'm not sure exactly what happened but this problem started after I did the aticonfig install. Any ideas? 

john

---

### Post by Legace on 2009-05-28
Try this:

> **gocek said:**
> Reboot PC and select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
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

