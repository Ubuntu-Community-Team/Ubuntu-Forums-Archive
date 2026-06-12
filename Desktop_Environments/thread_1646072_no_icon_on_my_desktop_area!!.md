---
title: "no icon on my desktop area!!"
date: 2010-12-15
forum: Desktop Environments
---

### Post by Pollyanna1 on 2010-12-15
After I installed ubuntu Notebook ver 10.10 I got no icons on my desktop, and I have to guess what icon is where!!!! 

Any Idea!!! I attached pictures for my desktop.

---

### Post by sikander3786 on 2010-12-15
Which graphics card is there? Did you install the proprietary drivers? If not, log out and click your name on the log in screen. Sessions menu will appear in the bottom of your screen. Choose ubuntu-desktop and login. Go to System > Administration > Additional Drivers and activate the current/recommended drivers if available. Then log back in ubuntu-netbook and see how it reacts.

If that doesn't help, post the output of this command.

```
lspci | grep VGA
```

---

### Post by Pollyanna1 on 2010-12-16
I will check that command, but this happened to me only when I install the Notebook edition, other wise it is OK with ubuntu 10.04 and 10.10 desktop ... do you think this problem form my card that Notebook version will not deduct the right one?

---

### Post by sikander3786 on 2010-12-16
Netbook Edition has got 3-D graphics so it might require some graphics hardware acceleration provided by the proprietary drivers. You might not have noticed that on the desktop edition. Let us know about your graphics card.

---

### Post by Pollyanna1 on 2010-12-16
This is what I got:

```

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

---

### Post by sikander3786 on 2010-12-17
Did you log in to ubuntu-desktop following post # 2 above and try to install the drivers?

---

### Post by Krytarik on 2010-12-17
> **Pollyanna1 said:**
> This is what I got:

```

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```
Your video-card is not supported anymore by the recent proprietary drivers, whether downloaded from the AMD/ATI-site or offered via Ubuntu-packages or the Ubuntu-X-Team-ppa.

I recommend trying the "Open Source Edge"-drivers, they should deliver a fairly good performance: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

---

### Post by Pollyanna1 on 2010-12-18
Every time I run ubuntu my screen freeze and I have to restart the computer again. Even I tried to install the OS into another HD and some thing, I could not be able to try installing any of the drivers, or just even brows the Internet. Is that from the card?

---

### Post by Krytarik on 2010-12-18
The Netbook Edition requires 3D-acceleration to work at all! So just try to install the "Open Source Edge" drivers with the commands at the link I posted earlier, from the console:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If successful reboot.

---

### Post by Pollyanna1 on 2010-12-19
Hey guys,,,, it works ... great support ... thanks very very very much.... =D>

---

### Post by Swagman on 2010-12-19
> **Pollyanna1 said:**
> After I installed ubuntu Notebook ver 10.10 I got no icons on my desktop, and I have to guess what icon is where!!!! 

Any Idea!!! I attached pictures for my desktop.


Awesome.. You should repackage that as ClueBuntu (Cluedo)


It was PollyAnna1.. With the mouse @ the desktop !!

---

### Post by Krytarik on 2010-12-19
> **Pollyanna1 said:**
> Hey guys,,,, it works ... great support ... thanks very very very much.... =D>
Great!:) You're welcome.

---

