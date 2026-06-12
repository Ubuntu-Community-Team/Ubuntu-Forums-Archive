---
title: "Flash Player Plug-in"
date: 2006-02-17
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2006-02-17
How do I install Flash Player (Macromedia Flash) Plug-in for Mozilla Firefox? When I use sudo apt-get install flashplayer-mozilla, I get the follwing message:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

---

### Post by kaamos on 2006-02-17
Have you enabled universe and multiverse? There are instructions here -> [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Perfect Storm on 2006-02-17
Or

Download flash: [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

```
cd /where/you/downloaded/it
tar zxvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer

```

When it ask for installing path:

/usr/lib/mozilla-firefox

---

