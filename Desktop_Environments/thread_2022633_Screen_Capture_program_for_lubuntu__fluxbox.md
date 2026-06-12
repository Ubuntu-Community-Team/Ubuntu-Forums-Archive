---
title: "Screen Capture program for lubuntu / fluxbox"
date: 2012-07-11
forum: Desktop Environments
---

### Post by uncle-c on 2012-07-11
I have lubuntu 12.04 installed and mostly run fluxbox. As a result I am unable to use the Gnome shell based screen capture programs. Could anyone suggest a decent program , imagemagick "import"  apart? Also want to avoid the in-built X snapshot.

---

### Post by Rodney9 on 2012-07-11
Hit printscreen key , it uses scrot.

[http://www.freesoftwaremagazine.com/articles/how_to_take_screenshots_with_scrot](http://www.freesoftwaremagazine.com/articles/how_to_take_screenshots_with_scrot)


For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by tumutanzi.com on 2012-07-11
I have to say, there are lots of screen capture programs, but almost none of them is very user friendly.

---

### Post by tumutanzi.com on 2012-07-11
I forgot to mention that I have to open Cheese to make my webcam work on my netbook.

---

### Post by Rick.B9 on 2012-07-11
You might try the lightweight package:
xfce4-screenshooter

```
sudo apt-get install --no-install-recommends xfce4-screenshooter
```the --no-install-recommends will keep it from installing extra cruft you don't want.  Alternatively, if you're using Synaptic, go to settings-->preferences-->general and untick 'consider recommended packages as dependencies.'

LXDE and XFCE are pretty good at dropping in light packages with few to no dependencies.  I'm not sure if you'll have to add the XFCE repository to your /etc/apt/sources.list, or not.

---

### Post by jmfal on 2012-07-11
shutter works 

```
  sudo apt-get install shutter
```

---

### Post by anonranger on 2012-07-27
I like Shutter

---

### Post by andrew.46 on 2012-07-28
I use fluxbox but not with lxde and some may be interested to know that it is easy enough to duplicate lxde's default image capture with the Print Screen button. Simply add the following to $HOME/.fluxbox/keys:


```

# Screenshot:
107 :ExecCommand scrot -q 100

```

or whatever scrot commandline you wish :).

---

