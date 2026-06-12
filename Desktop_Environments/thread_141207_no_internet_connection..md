---
title: "no internet connection."
date: 2006-03-07
forum: Desktop Environments
---

### Post by mr.digwell on 2006-03-07
Hi
I've just installed Breezy Badger after first downloading the files to install my usb adsl modem onto my windows partition. As I dont use either of my network cards for connecting to the internet, I skipped this stage of the install.
All seemed fine until I logged in. I get a warning window, saying :

   "Could not look up internet address for ubuntu. This will prevent
   GNOME from operating correctly. It may be possible to correct
   the problem by adding ubuntu to the file /etc/hosts"

I click the button "log in anyway" and when I try to do a sudo gedit on hosts I get the error :

   "sudo: unable to look up ubuntu via gethostbyname()"

can anyone help a frustrated newbie?

Thx.

---

### Post by nullmind on 2006-03-07
Can you use ndiswrapper?

---

### Post by jamesr on 2006-03-08
> "sudo: unable to look up ubuntu via gethostbyname()"

This is an error usually caused by a corrupt or missing /etc/hosts  file, note there is no name in the host name location > gethostbyname()

create or recreate the file

---

