---
title: "GDM is broken or not fully installed"
date: 2009-12-21
forum: Desktop Environments
---

### Post by Howie Spitz on 2009-12-21
Synaptic: 0 broken, 0 to install, 0 to remove.
I followed this page and got error at sed command.[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)
I have started XFCE, KDE, and GNOME sessions to work on this problem. I always am able to login to a working session but GNOME is always 2.2.80. 
I would just love to see that box I chose the default display manager again.
The login process is unpredictable now, I like to see the same login screen each time. Currently I am seeing 2.20 login splash. (I think)
gdmsetup  informs me GDM is not running.
Grateful for any help or advice, thank you.
/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed

---

### Post by lidex on 2009-12-21
Try running this command in your terminal:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

### Post by Howie Spitz on 2009-12-21
Thank you very much [lidex]("http://ubuntuforums.org/member.php?u=577099"). That gave me the option to choose gdm, gdm 2.20, kdm. I chickened out and just chose gdm. Things are back to the way it was after I installed.:)

---

### Post by spiderbatdad on 2009-12-21
[http://ubuntuforums.org/showthread.php?t=1331457](http://ubuntuforums.org/showthread.php?t=1331457)
This may work better for you...that is, making the symbolic link rather than editing /etc/gdm/gdm.conf
I'm using gdm-2.20 and prefer it for now.
```
cd /usr
sudo mkdir X11R6
cd X11R6
sudo ln -s /usr/bin bin
```

---

