---
title: "file association and icon change"
date: 2012-02-13
forum: Desktop Environments
---

### Post by centek1 on 2012-02-13
Hi,
Q1: how to change file assotiation - eg. I want all *.pdf shouild be correlated with PDF_SUPER_TOOL etc

Q2: how to change PDF doc icon from the "strange first page"-icon to the ACROBAT logo - want to have this for all PDF docs on my system.

---

### Post by Krytarik on 2012-02-13
> **centek1 said:**
> Q1: how to change file assotiation - eg. I want all *.pdf shouild be correlated with PDF_SUPER_TOOL etc
Regardless of what Ubuntu version you are running, right-click on *any* PDF file, choose "Properties", and under "Open With", change the default association.

> **centek1 said:**
> Q2: how to change PDF doc icon from the "strange first page"-icon to the ACROBAT logo - want to have this for all PDF docs on my system.
This depends on what Ubuntu version you are running:

[LIST]
[*]For versions up to Natty 11.04 (thus using Gnome 2), run:
```
gconftool-2 --set --type bool /desktop/gnome/thumbnailers/application@pdf/enable false
```
[*]For Oneiric 11.10 and later (thus using Gnome 3), run:
```
gsettings set org.gnome.desktop.thumbnailers disable "['application/pdf']"
```
[/LIST]
Thereafter, regardless of the Ubuntu version, clear the thumbnail cache (this includes the thumbnails of *all* mime-types):
```
rm -r ~/.thumbnails/*
```Regards.

---

### Post by centek1 on 2012-02-18
> **Krytarik said:**
> Regardless of what Ubuntu version you are running, right-click on *any* PDF file, choose "Properties", and under "Open With", change the default association.


This depends on what Ubuntu version you are running:

[LIST]
[*]For versions up to Natty 11.04 (thus using Gnome 2), run:
```
gconftool-2 --set --type bool /desktop/gnome/thumbnailers/application@pdf/enable false
```
[*]For Oneiric 11.10 and later (thus using Gnome 3), run:
```
gsettings set org.gnome.desktop.thumbnailers disable "['application/pdf']"
```
[/LIST]
Thereafter, regardless of the Ubuntu version, clear the thumbnail cache (this includes the thumbnails of *all* mime-types):
```
rm -r ~/.thumbnails/*
```Regards.

thanks... this solution is ubuntu specific...
how about universal solution for gnome on any other distributions?

---

### Post by Krytarik on 2012-02-18
> **centek1 said:**
> thanks... this solution is ubuntu specific...
how about universal solution for gnome on any other distributions?
This isn't Ubuntu-specific at all; simply consider the stated Gnome versions for whatever distro you are using. But regardless of that, remember that you've posted this into the "Ubuntu Forums"! ;-)

---

### Post by centek1 on 2012-02-19
yes, I know this is ubuntu forum...

problem is I dont have such tools you are refering to...

i have gnome 2

---

### Post by Krytarik on 2012-02-19
> **centek1 said:**
> problem is I dont have such tools you are refering to...

i have gnome 2
I'm using Gnome 2 too, with Lucid 10.04; but I obviously can't know if "gconftool-2" is available in the distro you are using, not even knowing its name till now. ;-)

---

