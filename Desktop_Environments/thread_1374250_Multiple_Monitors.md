---
title: "Multiple Monitors"
date: 2010-01-06
forum: Desktop Environments
---

### Post by Tom_T on 2010-01-06
Hi
I've got Ubuntu 9.10 installed with the Nvidia 185 drivers.

I have 2 TFT Screens. 1 is an LG L1710B (DVI) the other is a Medion MD41077EA (VGA)

Currently they are configured as one large desktop running at 2560x1024 pixels

Assuming I want the LG (on the left as I look at them) as the primary monitor, Is it possible to have them run as 2 unique desktops, both running at 1280 x 1024 ?

In XP ( :( sorry ) I use an app that allows me to move windows to the other monitor, or launch them on the other monitor. 
[http://www.realtimesoft.com/ultramon/overview/]("http://www.realtimesoft.com/ultramon/overview/")

Is anything like that available for Ubuntu ??

Thanks :)

---

### Post by Tom_T on 2010-01-09
Bump - anyone help with this ??

---

### Post by chewearn on 2010-01-09
Dual monitor configuration for nvidia is via nvidia-settings.  Before making any changes, it's a good idea to back-up your current working xorg.conf

```

sudo cp /etc/X11/org.conf /etc/X11/xorg.conf.working.backup

```Then, start nvidia settings with root:
```

gksudo nvidia-settings

```Your current configuration is called "Twinview". For independent dual monitor setup, find the "Separate X-screen".  Make sure to "save the configuration to xorg.conf" at the end, and restart X.

To launch application on the second monitor, you need to append the following environment to the launch command:
```

export DISPLAY=:0.1

```E.g. launch gedit on the second monitor:
```

export DISPLAY=:0.1; gedit

```

---

