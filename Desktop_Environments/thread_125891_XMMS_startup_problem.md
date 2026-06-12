---
title: "XMMS startup problem"
date: 2006-02-05
forum: Desktop Environments
---

### Post by playmobiel on 2006-02-05
I was trying to install the xmms-wma plugin with the source package and the .deb package, and now my xmms doesn't start anymore. I tryed te reinstall xmms, and i had still the same problem , i tryed te remove xmms completly, and install it again , still the same problem. I removed the .deb xmms-wma package and installed xmms again , still the same problem. When i try to start xmms in the console, it doesn't give output. I removed the ~/.xmms/ dir, because i could  start xmms as root user. When i removed that dir , and i start xmms again , the console diplays this :

> *****@****:~$ xmms

Gtk-WARNING **: Kan module in module_path: "liblighthouseblue.so" niet vinden,

Gtk-WARNING **: Kan module in module_path: "liblighthouseblue.so" niet vinden,



All help is welcome

Thanks , 

Playmobiel

Edit : beep-media-player also doens't work

---

### Post by Perfect Storm on 2006-02-05
Have you gtk2-engines-lighthouseblue installed?

```
sudo apt-get install gtk2-engines-lighthouseblue
```

Did you remove the /.xmms from /home/<user name> ?

---

### Post by playmobiel on 2006-02-05
Yes , from the user home dir. And gtk2-engines-lighthouseblue is installed 
But i did this , and now xmms works aigain , very strange.

#sudo apt-get -f install
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Vereisten worden verbeterd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  gimp
Voorgestelde pakketten:
  gimp-help-en gimp-help libgimp-perl gimp-data-extras
Aanbevolen pakketten:
  gimp-svg
De volgende pakketten zullen opgewaardeerd worden:
  gimp

Thanks anyway :D

---

