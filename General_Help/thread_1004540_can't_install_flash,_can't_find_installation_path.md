---
title: "can't install flash, can't find installation path"
date: 2008-12-07
forum: General Help
---

### Post by david.d.38 on 2008-12-07
hey guys,

i'm trying to install flash player, but i don't know where to install it to. when i run the installation in the terminal, i get this: "Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):" now i'm not sure where to install flash to. i've tried numerous places, but i always get a warning saying: "WARNING: Please enter a valid installation path." or "WARNING: /home/dave/Desktop/dir= /usr/lib/firefox/plugins is not a directory."

---

### Post by mk1w86 on 2008-12-07
Make sure the restricted repositories are enabled and run

```
sudo apt-get install ubuntu-restricted-extras
```

This will install flash and many other useful but non free packages such as java and codecs. :)

---

### Post by the yawner on 2008-12-07
Or if you want to just install the flash plugin:
```

sudo apt-get install flashplugin-nonfree

```

Alternatively, Adobe offers the latest version as an easy to install deb file.
[Link]("http://get.adobe.com/flashplayer/?promoid=BUIGP")
Just select deb for 8.04 plus. Download the file and double-click it and gdebi will install it for you.

---

### Post by Matt Yun on 2008-12-07
> **david.d.38 said:**
> hey guys,

i'm trying to install flash player, but i don't know where to install it to. when i run the installation in the terminal, i get this: "Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):" now i'm not sure where to install flash to. i've tried numerous places, but i always get a warning saying: "WARNING: Please enter a valid installation path." or "WARNING: /home/dave/Desktop/dir= /usr/lib/firefox/plugins is not a directory."

In Ubuntu, the proprietary Adobe flashplayer binary resides under /**var/lib/flashplugin-nonfree/**, and is symlinked with **/etc/alternatives/mozilla-flashplugin**

BTW, to install the [64-bit Flashplayer 10 alpha version]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz"), download it and do this:

```
tar xvzf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /var/lib/flashplugin-nonfree
sudo rm /etc/alternatives/mozilla-flashplugin
sudo ln -s /var/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/mozilla-flashplugin
```

---

