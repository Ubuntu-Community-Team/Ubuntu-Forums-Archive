---
title: "HOw to find new themes for MATE 1.6.0"
date: 2013-09-26
forum: Desktop Environments
---

### Post by suomalainen on 2013-09-26
Ubunteros,

In Mate under System-->Preferences-->Appearance it's possible to change theme appearance.

How and where can I find the "Dust" one that was available in 10.04?

Thanks!

---

### Post by Frogs Hair on 2013-09-26
Try the following command. The package includes Dust-Dust Sand & New Wave. These are gnome 2 themes and I am not positive they work with mate.

```
sudo apt-get install gnome-themes-ubuntu 
```

---

### Post by tgalati4 on 2013-09-26
There is a *mate-themes* package, although I have no idea what is in it:

tgalati4@Mint14-Extensa ~ $ apt-cache policy mate-themes
mate-themes:
  Installed: (none)
  Candidate: 1.4.0-1+precise
  Version table:
     1.4.0-1+precise 0
        700 [http://packages.linuxmint.com/](http://packages.linuxmint.com/) nadia/import amd64 Packages

---

### Post by suomalainen on 2013-09-29
Great advice! Thank you. worked!

---

### Post by checor on 2013-09-30
As it said above, install mate-themes.

You can use almost any GNOME 2.x themes also, look for gnome-look.org for more eyecandy.

---

### Post by vasa1 on 2013-09-30
> **suomalainen said:**
> Great advice! Thank you. worked!

What worked? It isn't clear.

---

