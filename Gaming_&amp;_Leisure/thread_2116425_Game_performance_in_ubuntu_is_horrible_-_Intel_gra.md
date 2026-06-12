---
title: "Game performance in ubuntu is horrible - Intel graphics 965"
date: 2013-02-15
forum: Gaming &amp; Leisure
---

### Post by jobbs on 2013-02-15
In my notebook the gaming performance with the integrated gpu Intel Graphics 965 in Ubuntu 12.04 64bits, compared with Windows 7 32bits is horrible, the fps is much slow. For example, in a simple SNES emulator with maximum settings active, using Windows 7 i get 60fps throughout the whole game, already in ubuntu: 29-35 fps. Does are the drivers in ubuntu or is the Unity 3D that is stealing fps of the games?

I thank any help. :p

---

### Post by Perfect Storm on 2013-02-16
Try see if you get better performance with the lastest intel driver;

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
```

reboot.

---

### Post by LillyDragon on 2013-02-16
Yeah, Unity does that to my Intel hardware too; I can't get a decent frame rate on ZSNES no matter what I try. The only way I can fully enjoy SNES titles and ioquake3-based games on Ubuntu is to use the XFCE WM, which I stay logged into most of the time anyway.

All of my other games don't seem that affected by Unity, but those apps specifically lose a lot of performance compared to running them in XFCE. Even worse, going full-screen involves it flipping out for five seconds before it's fully switched over to the lower resolution, whereas on XFCE the transition is lightning fast and smooth.

---

### Post by redpower1989 on 2013-02-21
> **Artificial Intelligence said:**
> Try see if you get better performance with the lastest intel driver;

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
```reboot.

Hi . i installed the latest intel driver and i have problems. Do you know how can i went back? Or any other ideas??

---

### Post by Perfect Storm on 2013-02-21
To downgrade:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

---

### Post by redpower1989 on 2013-02-21
> **Artificial Intelligence said:**
> To downgrade:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```


Thanks for your answer  but i still have problems . Mostly with colours.

---

### Post by Perfect Storm on 2013-02-22
> **redpower1989 said:**
> Thanks for your answer  but i still have problems . Mostly with colours.

Better start a new thread in our Hardware forum about this issue as you may hit a bug or something. I don't have intel so I can't help you further. 
(Using nvidia on all my machines).

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

