---
title: "Unable to select screen resolution higher than 1024 by 768"
date: 2006-09-06
forum: Desktop Environments
---

### Post by scumble on 2006-09-06
Greetings. I've had no trouble installing Ubuntu desktop - it was very quick in fact, however, the slight problem I have is that I can't select a screen resolution of 1280 by 1024 - the native resolution of my LCD monitor.
I checked Xorg.conf for the required screen modes and they were all present, and this is where my knowledge about how screen modes are set up ends. Why exactly can't the screen resolution app provide access to all the modes in Xorg.conf?

Note that I have an NV43 card (Nvidia 6600GT), in case that helps.

---

### Post by Druidor on 2006-09-06
Try dropping the colour settings from 24 down to 16.

I had this on a test machine that I was trying to get 1280 resolution but it just would not display it in the gui.

try the following links that I was suggested when I asked

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index....0Configuration](https://wiki.caosity.org/tiki-index....0Configuration)

basically do the following:

**Backup your configuration file**
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

**Run the config program**
```

sudo dpkg-reconfigure xserver-xorg

```

**Restart the gui**

[CTRL]+[ALT]+[Backspace]

---

### Post by hraposo on 2006-09-06
Try:
sudo dpkg-reconfigure xserver-xorg
and select the resolutions tat's you want.

---

