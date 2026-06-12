---
title: "Manually download vlc"
date: 2009-04-21
forum: General Help
---

### Post by mubbashar on 2009-04-21
i am new to ubunto .please tell from where i manually download vlc and how to intall it and also tell what is gnome i read it many places...

---

### Post by Anthon on 2009-04-21
Open a terminal and type
   sudo apt-get install vlc

---

### Post by mubbashar on 2009-04-21
i want to download first not install

---

### Post by ad_267 on 2009-04-21
Or Applications - Add/Remove and search for VLC.

If that doesn't work you might have to go to System - Administration - Software Sources and check that Universe and Multiverse are ticked.

[Gnome]("http://en.wikipedia.org/wiki/GNOME") is the desktop environment used by Ubuntu. It includes the desktop, panels at the top and bottom of the screen, the file browser and many other applications.

---

### Post by ad_267 on 2009-04-21
> **mubbashar said:**
> i want to download first not install

aptitude download vlc

---

### Post by mubbashar on 2009-04-21
in where location these download file are placed can u tell me?as u know i am new to ubunto so i am very intersting in knowing this.

---

### Post by stoneage on 2009-04-21
It should download to whichever directory you were in at the time, so probably your home directory.

---

### Post by mubbashar on 2009-04-21
i have download vlc from internet please tell me how to install them i have no idea of using terminal.it is tar.bz2 file

---

### Post by stoneage on 2009-04-21
Use ```
aptitude download vlc
```then install the .deb

it will be simpler to install, easier to remove and should run better.

From the vlc website - [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

You may have downloaded source code, if you want to build it you will require more specific advice.

To untar use ```
tar -jxvf package.tar.bz2
```
You can get more info on usage from ```
man tar
```

---

### Post by Anthon on 2009-04-21
> **mubbashar said:**
> i want to download first not install
sudo apt-get install --download-only vlc
only downloads

---

### Post by mubbashar on 2009-04-21
thankssssssssss

---

