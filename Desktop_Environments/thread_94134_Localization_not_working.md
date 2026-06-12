---
title: "Localization not working ?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by karl_kashofer on 2005-11-23
Hi !

I am having problems getting localization to work.

For example, my system locale is set to de_AT:

beka@beka-kubuntu:~$ locale
LANG=de_AT.UTF-8
LC_CTYPE="de_AT.UTF-8"
LC_NUMERIC="de_AT.UTF-8"
LC_TIME="de_AT.UTF-8"
LC_COLLATE="de_AT.UTF-8"
LC_MONETARY="de_AT.UTF-8"
LC_MESSAGES="de_AT.UTF-8"
LC_PAPER="de_AT.UTF-8"
LC_NAME="de_AT.UTF-8"
LC_ADDRESS="de_AT.UTF-8"
LC_TELEPHONE="de_AT.UTF-8"
LC_MEASUREMENT="de_AT.UTF-8"
LC_IDENTIFICATION="de_AT.UTF-8"
LC_ALL=

However, when i start gimp its in english.

Same is true with "LANG=de_DE gimp"

This could be a problem with gnome apps, as all KDE apps are correctly localized.

Any ideas anyone ?

Cheers,
Karl

---

### Post by sdr_ar on 2005-11-23
If your refer to the menus, and interface language, LANG=de_AT won't translate Gimp.
Now well, if you refer to the distribution of your keyboard, that's other issue. To see that go to K menu -> System Settings -> "Regional and accesibility" and change your regional configuration ank keyboard layout.
Regards.

---

### Post by karl_kashofer on 2005-11-24
Hi !

[QUOTE=sdr_ar]If your refer to the menus, and interface language, LANG=de_AT won't translate Gimp.[/QUOTE]

So what would ?

Thanks,
Karl
PS: i tried de_DE as you can see from my original post

---

### Post by karl_kashofer on 2005-11-25
Hi !

I found the reason for this behaviour. My LANGUAGE variable was set to "en_DE" which obviously does not exist.
No idea how that happened, but "dpkg-reconfigure locales" and the localization setting in KDE do not have any effect on this variable.

I changed it to "de_DE" in /etc/environment and now all is well.

Cheers,
Karl

---

