---
title: "How To Install an X System for Ubuntu Server?"
date: 2007-05-27
forum: Desktop Environments
---

### Post by neognat on 2007-05-27
I just installed Ubuntu Server 7.04 and would like to use a desktop environment, like Gnome. As far as I can tell, the server edition does not come with a gui like the desktop versions do. I've been googling for hours and haven't found any guide or other help in how to install one. I've been thinking Gnome, but at this point I'm willing to try anything that will work. Most distributions come with the desktop environment as part of the basic installation. Evidently, the server edition does not. I don't mind doing the reading if someone could point me toward a good guide or other resource.

---

### Post by Bluecircle on 2007-05-27
Use apt-get to install the packages?

ex:


```
sudo apt-get install gnome
``` 

```
sudo apt-get install xorg
```

```
sudo apt-get install xserver-xorg
``` 

```
sudo apt-get install gdm
```

```
sudo apt-get install nautilus
```

```
sudo apt-get install metacity
``` 


etc...

---

### Post by neognat on 2007-05-27
Thanks for the information. The problem I had with apt-get is that I didn't know the package names. After I posted, I ran aptitude and am installing Gnome now. It has been running for more than 10 hours and looks like it has a couple more days to run at a download rate of about 40 kB/s.

---

### Post by RedSquirrel on 2007-05-27
All of the Ubuntu Desktop editions come with a graphical environment. The server edition does not. For GNOME, you could just install the ubuntu-desktop metapackage:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```The other metapackages for desktops are xubuntu-desktop, kubuntu-desktop and edubuntu-desktop.

By the way, you can put package names on one apt-get line if you prefer.

---

### Post by Bluecircle on 2007-05-27
> **RedSquirrel said:**
> All of the Ubuntu Desktop editions come with a graphical environment. The server edition does not. For GNOME, you could just install the ubuntu-desktop metapackage:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```The other metapackages for desktops are xubuntu-desktop, kubuntu-desktop and edubuntu-desktop.

By the way, you can put package names on one apt-get line if you prefer.

Yeah that is easier, forgot about that.

---

### Post by neognat on 2007-05-27
I think I'm going to reinstall the OS and try again. The install has been running for about 18 hours and hitting speeds of almost 200 kB/s and it's still at only 42 percent complete. It must be 5 GB of data or more by now. It's hard to believe that Gnome is that big... there must be something wrong. It can't be this difficult.

---

### Post by RedSquirrel on 2007-05-28
> **neognat said:**
> I think I'm going to reinstall the OS and try again. The install has been running for about 18 hours and hitting speeds of almost 200 kB/s and it's still at only 42 percent complete. It must be 5 GB of data or more by now. It's hard to believe that Gnome is that big... there must be something wrong. It can't be this difficult.
GNOME is not that big, so something must be wrong. The entire desktop installation of Ubuntu (i.e., the Desktop CD) is about 2 GB.

Perhaps the server you are using for the repositories is slow. Sometimes that happens. If you're going to install GNOME anyway, maybe you should consider downloading the Desktop version of Ubuntu from a fast mirror (unless you especially wanted the server edition).

Another possibility is to download a small window manager instead of GNOME (e.g., Fluxbox or IceWM). You'll still need xorg, but it will lower the size of your download. Up to you...

---

