---
title: "No Sound on Utube on Firefox"
date: 2006-09-23
forum: Desktop Environments
---

### Post by cnferntreegully on 2006-09-23
I have installed necessary plugins for Firefox including Flash.  When opening certain video on Utube I do not get sound.  On some other videos I have both video AND audio.

What is the best plugin to use for utube?? (so I get sound)

---

### Post by pay on 2006-09-23
Try```
sudo aptitude install flashplugin-nonfree
sudo update-flashplugin
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```and then change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```and close down firefox and try again.
Goodluck

---

### Post by cnferntreegully on 2006-09-24
Legend!!
It works - thanks very much!

---

### Post by findus on 2006-09-25
Fantastic -works for me too!

---

### Post by conjurer on 2006-09-25
After doing:
sudo update-flashplugin

I get:
automatic installation failed due to network problems or upstream changes

---

