---
title: "Install Wine"
date: 2007-03-21
forum: Gaming &amp; Leisure
---

### Post by blockdude14 on 2007-03-21
Is there a easy and safe way to install Wine on the 64 bit processor Ubuntu? I really want my applications and games to work on my Ubuntu since my Windows expired. :confused:

---

### Post by AJB2K3 on 2007-03-21
[www.google.com](www.google.com)
and 
SEARCH THE FORUMS !
Thats how i found out how to install wine after it wouldn't appear in the repo's:lolflag:

---

### Post by dmn_clown on 2007-03-22
> **blockdude14 said:**
> Is there a easy and safe way to install Wine on the 64 bit processor Ubuntu? I really want my applications and games to work on my Ubuntu since my Windows expired. :confused:

two options:  backport the amd64 wine package from Debian sid or wait for Feisty.

---

### Post by erwinquita on 2007-03-22
Wine on  Ubuntu AMD64

This is a quick hack to install the 32-bit Ubuntu Wine package onto AMD-64 until a working 64 bit package can be made available in the APT repository.

**Instructions:**
First, you need several 32-bit libraries like [COLOR="DarkRed"]ia32libs[/COLOR] and [COLOR="DarkRed"]lib32asound2[/COLOR] (if you're using ALSA). Install these with apt-get or synaptics.

Then, [download the Wine package]("http://wine.budgetdedicated.com/archive/index.html"). You want the [latest version]("http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.33~winehq0~ubuntu~6.10-2_i386.deb") available for either dapper or edgy, depending on which one you're using. New versions are released about twice a month.

Save the file to your desktop.

Open a terminal. You may have to edit the command to reflect the version number of the .deb you downloaded. You will need to have the various ia32-libs packages installed already.

```
cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb
```

You can delete the .deb file from your desktop when you're done.

Hope this helps! 

You can also go to our linux community [[COLOR="DarkRed"]www.ibatayo.com[/COLOR]]("http://www.ibatayo.com"). we have lots of how-to there like installing dreamweaver etc...

---

### Post by lakersforce on 2007-03-22
If you are only going to run 32-bit programs, you should consider using the i386 version of ubuntu instead. That would save you a whole lot of headache.

---

