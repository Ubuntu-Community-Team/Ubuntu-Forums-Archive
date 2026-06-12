---
title: "Upgrading Kernel"
date: 2005-08-04
forum: Desktop Environments
---

### Post by adamb10 on 2005-08-04
How does one install a new kernel from apt-get?

---

### Post by heimo on 2005-08-04
Which one do you want to install? If you want just something else than stock 386-kernel, you can for example:
 ```

sudo apt-get install linux-686
sudo apt-get install linux-k7

``` 

Or search:
 ```
apt-cache search ^linux-image

``` 
and install one of those, just like abowe. If everything went without errors, just reboot.

Benefit of first approach is that you get new versions automaticly. Defining exact version means you have to install the latest yourself when security bugs are fixed in kernel.

---

### Post by adamb10 on 2005-08-04
[QUOTE=heimo]Which one do you want to install? If you want just something else than stock 386-kernel, you can for example:
 ```

sudo apt-get install linux-686
sudo apt-get install linux-k7

``` 

Or search:
 ```
apt-cache search ^linux-image

``` 
and install one of those, just like abowe. If everything went without errors, just reboot.

Benefit of first approach is that you get new versions automaticly. Defining exact version means you have to install the latest yourself when security bugs are fixed in kernel.[/QUOTE]
 How do you download the latest stock?

---

### Post by adamb10 on 2005-08-04
[QUOTE=heimo]Which one do you want to install? If you want just something else than stock 386-kernel, you can for example:
 ```

sudo apt-get install linux-686
sudo apt-get install linux-k7

``` 

Or search:
 ```
apt-cache search ^linux-image

``` 
and install one of those, just like abowe. If everything went without errors, just reboot.

Benefit of first approach is that you get new versions automaticly. Defining exact version means you have to install the latest yourself when security bugs are fixed in kernel.[/QUOTE]
 So I installed 2.6.11-1 but when I reboot xorg spits out:

no screens found

---

### Post by heimo on 2005-08-04
Have you installed binary drivers for ati or nvidia? You have to do that per kernel. If you haven't - reconfigure X.
 ```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by adamb10 on 2005-08-04
Yeah, I installed the drivers as mentioned in ubuntu guide.

---

### Post by adamb10 on 2005-08-04
Ok so I didn't install the drivers.

I did the xorg thing and now my scroll wheel won't work and the text is so blury.

---

### Post by heimo on 2005-08-04
[QUOTE=adamb10]Ok so I didn't install the drivers.

I did the xorg thing and now my scroll wheel won't work and the text is so blury.[/QUOTE]

Check what different versions you have of your xorg.conf:
ls -al /etc/X11/xorg.conf*

And copy (using sudo cp [from] [to]) to make a copy of your current xorg.conf and copy some previous version to xorg.conf. Then reinstall binary drivers and restart gdm (sudo /etc/init.d/gdm restart).

---

