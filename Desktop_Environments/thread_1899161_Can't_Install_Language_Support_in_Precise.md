---
title: "Can't Install Language Support in Precise"
date: 2011-12-23
forum: Desktop Environments
---

### Post by ping-wu on 2011-12-23
I am unable to install language support (Chinese and Japanese) in Ubuntu 12.04 (fully updated).  The installer would freeze.  Does anyone have any info?  Thanks.

---

### Post by kamereon on 2012-04-29
Did you get it to work?
I can't install the japenese language pack on 12.4 32-Bit.
when selecting 'japanese' under 'add language', gnome-language-selector will just say "python-gtk2 already installed" and do nothing at all.

aah, installing other languages used to work so well in older versions of ubuntu...:icon_frown:

---

### Post by konDA on 2012-05-06
Hello,
I have similar problem. I upgraded from Oneiric (64 bit). After upgrade everything was in English. So in Language Support I removed English, and check Czech language to install. But after reboot everything remains in English. Although the Language Support shows there is only Czech language installed :-o

Andrew

---

### Post by muzah on 2012-05-09
I have the same problem.
The fact is I have setup a fresh install of Precise on two Lenovo Laptop, exactly the same. On the first one, the french language is normaly setup and the second one, despite of the correct setup, it's always the english that is displayed.

I haven't find any answer for now.

---

### Post by muzah on 2012-05-09
I found a solution :

```
sudo apt-get install localepurge
```

and select the language you want to use.
Then reboot.

If as on my laptop, this op is not working after rebooting, I have restart localepurge :

```
sudo dpkg-reconfigure localepurge
```

And it's fine !

Before that, my locale file was :

```
LANG="en_US.UTF-8"
LANGUAGE="en"
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_MONETARY="fr_FR.UTF-8"
LC_PAPER="fr_FR.UTF-8"
LC_IDENTIFICATION="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADDRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
```

That's why the default language was EN.

---

