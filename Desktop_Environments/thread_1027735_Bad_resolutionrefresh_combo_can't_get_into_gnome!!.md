---
title: "Bad resolution/refresh combo can't get into gnome?!?!"
date: 2009-01-01
forum: Desktop Environments
---

### Post by tricky37 on 2009-01-01
I recently installed drivers for an ATI Radeon 9000 in Ubuntu 8.10...
I believe it was my first restart after that and i got an error and had to boot in low graphics mode.  That set me in 1280X1024 when i got in, i went to res settings and dropped to 1024X768 and that scrambled the screen.  Now i can't get anything past login screen, once i log in it changes resolution and scrambles screen.  i have changed, deleted etc etc to xorg.conf and tried the dpkg reconfigure....

I have exactly the same problem as this post:
[http://ubuntuforums.org/showthread.php?p=5619324](http://ubuntuforums.org/showthread.php?p=5619324)

however I don't seem to have the same monitor settings file....

any advice would be VERY appreciated

I am desperate....

---

### Post by stderr on 2009-01-01
I would try purging your installed drivers and start over with driver installation. 

I reckon:

```
sudo apt-get purge fglrx*
```

Maybe also (remove all pre-compiled ATi kernel modules):

```
sudo rm -r /var/lib/dkms/fglrx
```

Then download the latest ATi driver again (you'll probably want [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run") if you're running 32-bit). 

You can then 

```
cd path/to/downloaded/file 
chmod +x ati-driver-installer-8.28.8.run
sudo ./ati-driver-installer-8.28.8.run
```

HTH

---

