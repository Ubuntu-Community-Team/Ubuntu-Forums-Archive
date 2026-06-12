---
title: "Brightness issues with Ubuntu"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Zotova on 2006-06-04
Firstly in Kubuntu this problem does not exist - the brightness is the same level as it is in Windows and no settings have to be altered. However with Ubuntu my laptops screen is too bright for my liking.

This is a new problem which only occurs in Dapper, in Hoary and Breezy the brightness has stayed at the right level in either window manager (KDE/Gnome).

I've done a bit of searching and found a Breezy thread for brightness controls for sony vaio laptops. Basically the following line of code alters the brightness:

echo 4 >> /proc/acpi/sony/brightness

The default is 5 - at the moment I have to issue this every time I login to gnome (highly annoying). In the thread I referred to above there is a default setting:

echo 4 >> /proc/acpi/sony/brightness_default

That is supposed to make 4 the default level of brightness, of course it doesn't work - even though if I open a root nautilus the file does actually show as saying 4.

Basically, has anyone else got a vaio who is having brightness issues with Dapper? Or does anyone know how I can issue the command (echo 4 >> /proc/acpi/sony/brightness) at the Gnome login automatically without any actions required on my behalf?

I've tried putting a a file with that line of code in it within /etc/init.d folder and then added it to the start up, however that seems to be ineffective.

Any ideas?

Thanks.

---

### Post by Zotova on 2006-06-04
Nevermind, found the settings - in the power settings of all places ](*,) 

Wouldn't an option in the display settings be better?

---

