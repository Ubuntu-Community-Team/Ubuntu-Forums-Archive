---
title: "Lock the background with gconftool gnome classic"
date: 2012-09-10
forum: Desktop Environments
---

### Post by nerolokki on 2012-09-10
Hello, I use gnome classic, I need to lock the desktop background image so that it can not be changed by the user.

In the previous version of gnome (ubuntu 10.04) I used this command and I set the file image.jpg as the background can not be changed:
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/immagine.jpg"

In the new version (gnome classic on ubuntu 12.04) does not work I tried to find information about it but I really cant find how to set mandatory key values &#8203;&#8203;with dconf.

Is there some other utility to operate on keys?
With gnome classic I need use dconf or gconf?
You know tell me some guide or site that explains mandatory keys ?

thanks

sorry for my bad english

---

### Post by Krytarik on 2012-09-10
Please see if the method described under "Lockdown" in this doc works:

[https://live.gnome.org/dconf/SystemAdministrators](https://live.gnome.org/dconf/SystemAdministrators)

Regards.

---

### Post by nerolokki on 2012-09-19
Thanks for the reply.
The link you gave me is very helpful, but unfortunately applying what is written in the summary, the system does not start lightdm.
In the x11 log file i find "nox11 mode", no other errors are reported.

Can someone help me ?

---

### Post by nerolokki on 2012-09-19
I do it.
I created a folder for the local db.

==> / Etc/dconf/db/local.d/00_site_settings <==

In my case contains the same code

==> / Etc/dconf/db/site.d/00_site_settings <==

thx

---

