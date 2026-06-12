---
title: "Playing MPegs and .mov's inside Firefox"
date: 2006-05-21
forum: Desktop Environments
---

### Post by Tipo on 2006-05-21
Is there a plugin for Firefox that allows me to play .mpgs and .mov's inside Firefox, without having to download the file?

Sometimes downloading the file and viewing it in Totem is cumbersome:-k

---

### Post by Fass on 2006-05-21
```
sudo apt-get install mplayerplug-in w32codecs
```

You may need to edit your ~/.mplayer/config file to say something like 

```
 # Write your default config options here!
vo=xv,x11
ao=esd
zoom=yes
```
if you get choppy video or sound issues.

---

### Post by Tipo on 2006-05-22
Great! Thanks :)

---

### Post by suspend on 2006-05-24
I tried the above and get:

E: Couldn't find package mplayerplug-in

---

### Post by adamkane on 2006-05-24
Pressing a link, and opening in Totem is the easiest way.

Install mplayer-plugin, if you prefer:
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox)

gxine (xine-ui) plays the most formats:
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29)

---

