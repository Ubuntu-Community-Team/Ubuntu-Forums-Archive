---
title: "Tried upgrading Cinnamon to V3 and now it's totally hosed."
date: 2017-07-24
forum: Desktop Environments
---

### Post by mslinklater on 2017-07-24
Hi - I tried installing Cinnamon (2.8) a few days ago and decided I liked it so much I would try V3. I added the ppa as detailed here:[https://www.unixmen.com/install-cinnamon-3-0-ubuntu-16-04-lts/](https://www.unixmen.com/install-cinnamon-3-0-ubuntu-16-04-lts/) and when I logged in Cinnamon crashed,

So I decided to try to revert to V2.8.

sudo apt-get purge cinnamon cinnamon-core
sudo apt-get autoremove

I then removed the embrosyn ppa and reinstalled cinnamon:

sudo apt-get install cinnamon cinnamon-core

When I tried to use Cinnamon it crashed at login. syslog said it was having problems parsing some .desktop files inside /usr/share/applications/ so I deleted them and uninstalled cinnamon again.

I have once again reinstalled cinnamon and it is now failing to start the session. syslog is telling me it is unable to find required components 'cinnamon-settings-daemon' and 'cinnamon-screensaver'.

I fear I've got my system in a mess. Can anyone help ? I'm quite new to Ubuntu and I'm really at an end as to how to clean this mess up....

Thanks.

Ubuntu 16.04

---

### Post by Frogs Hair on 2017-07-24
Was version 2.8 in the Ubuntu repository or installed from another source ?

---

### Post by mslinklater on 2017-07-24
2.8 was from the default Ubuntu repository. It's currently at 2.8.6.

---

### Post by Frogs Hair on 2017-07-24
> I then removed the embrosyn ppa  By what method, PPA purge or another ?

---

### Post by Frogs Hair on 2017-07-24
Try the following from the terminal one command at a time. ```
sudo apt install ppa-purge
``````
sudo ppa-purge ppa:embrosyn/cinnamon
``````
sudo apt update
``` ```
sudo apt install --reinstall cinnamon
```

---

