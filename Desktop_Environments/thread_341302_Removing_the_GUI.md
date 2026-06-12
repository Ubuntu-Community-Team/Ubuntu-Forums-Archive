---
title: "Removing the GUI"
date: 2007-01-18
forum: Desktop Environments
---

### Post by Lutherian on 2007-01-18
Greetings.

I have an old PC whcih I've installed Ubuntu on. It works nicely, but slows down after a while .. not neccisarlity a bad thing 'cos it's encouraging me to use the terminal / shell  more and more. To rid myself of the GUI over-reliance (which is very nice otherwise) I tried to edit the initab file, changing from runlevel 5 (gui) to runlevel 3 (text mode) despite this, the system still boots in GUI mode, very ironic - a few years ago I was trying Red Hat Linux and had the opposite problem :) at a time when I *really* still needed the GUI.

---

### Post by taurus on 2007-01-18
```
sudo aptitude remove gdm
```

---

### Post by bswilson on 2007-01-18
> **Lutherian said:**
> To rid myself of the GUI over-reliance (which is very nice otherwise) I tried to edit the initab file, changing from runlevel 5 (gui) to runlevel 3 (text mode) despite this, the system still boots in GUI mode, very ironic 

Well, if you want to get rid of the GUI altogether, just remove the package parent:

```
sudo apt-get remove ubuntu-desktop
```

---

### Post by Lutherian on 2007-01-18
Thank you for that! (Unexpectly fast response.) I never realised it could be that simple. For the older machine I will definitely go with that. 

Thanks again.

---

### Post by ComplexNumber on 2007-01-18
> **bswilson said:**
> Well, if you want to get rid of the GUI altogether, just remove the package parent:

```
sudo apt-get remove ubuntu-desktop
```
removing that that does nothing (other than merely removing the metapackage). its just a metapackage.

---

