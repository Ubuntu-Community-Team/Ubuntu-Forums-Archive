---
title: "kdm login manager doesn't appear as configured"
date: 2005-10-23
forum: Desktop Environments
---

### Post by arubin on 2005-10-23
I have gone to settings/system/login manager to configure the login screen the way I want it. The changes have obviously been saved but the login screen is not changed. My chosen background appears in the interval between clicking to login and the desktop appearing.

Truth to say the login manager for kubuntu looks more like gdm than kdm to my untutored eye.

How to I get a proper kde login screen?

Thanks

---

### Post by red_plague on 2005-10-24
If the login screen has a lot of brown in it, and if the logOut menu from kde only has "log out" and no reboot or Shutdown entry then: you are using GDM and not KDM, to use kdm do:
sudo dpkg-reconfigure kdm
and select kdm, then reboot

---

### Post by Psimon on 2005-10-24
I have this same problem.

I'm one hundred percent sure that KDM is the default log in manager (GDM isn't installed) but the the configuration tool in System Settings does nothing to change the appearance. Likewise my chosen background briefly appears when I log in and that's it. I wondered if I was missing some component but a search in synaptic was fruitless.  It should work because I got it working on other Linux distros. 

I'd also be interested to hear if anyone knows how to resolve this.

---

### Post by Dromio on 2005-10-24
Only way I've been able to configure KDM is by editing the files by hand.  The config files are in "/etc/kde3/kdm"

---

### Post by Thorsten on 2005-10-24
[quote=arubin]I have gone to settings/system/login manager to configure the login screen the way I want it. The changes have obviously been saved but the login screen is not changed. My chosen background appears in the interval between clicking to login and the desktop appearing.

Truth to say the login manager for kubuntu looks more like gdm than kdm to my untutored eye.

How to I get a proper kde login screen?
[/quote] 
I found this pretty confusing, too. Kubuntu uses a theme for KDM, which (AFAIK) can't be configured by a GUI. To get the configurable vanilla KDM we know and love, edit /etc/kde3/kdm/kdmrc and change "UseTheme = true" to "UseTheme = false".

BTW, this was previously discussed in [http://ubuntuforums.org/showthread.php?t=23110]("http://ubuntuforums.org/showthread.php?t=23110")

HTH,
Thorsten

---

### Post by arubin on 2005-10-26
Thanks Thorsten. That did the trick.

Alan

---

