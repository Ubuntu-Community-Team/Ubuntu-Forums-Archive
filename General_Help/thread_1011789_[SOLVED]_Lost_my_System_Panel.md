---
title: "[SOLVED] Lost my System Panel"
date: 2008-12-15
forum: General Help
---

### Post by Arrgoss on 2008-12-15
I have lost my Ubuntu System Panel and cannot get it back. I was messing around because my wireless icon had mysteriously disappeared from my panel (but that's now a secondary problem) and I totally removed the system panel (right click on the bar --> "remove desktop panel"). The whole "bar" disappeared and now I'm trying to get it back.

When I type "gnome-panel" in the terminal the answer is "A panel is already running", but there is no visible panel on my desktop.

I need help, please!

---

### Post by howefield on 2008-12-15
You still got the bottom bar ?

Right click on it and select New Panel, then right click that one and select Add to Panel to put back the icons.

---

### Post by Arrgoss on 2008-12-15
Hey, thanks. I figured that out in the meantime. I added one new panel and customize it from the scratch. Thanks!

Any idea on how to get back my wireless notification icon? (My notification area is there, but no wireless icon on it)

---

### Post by howefield on 2008-12-15
Is that not fixed simply by adding the notification icon to the panel ?

---

### Post by Arrgoss on 2008-12-15
> **howefield said:**
> Is that not fixed simply by adding the notification icon to the panel ?

That's what it should be. I have the notification icon added, and the rest of icons show up (bluetooth, network connection... ) but the wireless icon which used to be there disappeared.

---

### Post by 3rdalbum on 2008-12-15
Try logging out and logging back in again; that should start the applet again.

---

### Post by Mads_7 on 2008-12-15
I think it's because networking applet isn't part of the Notification Area.
Try adding the Network Monitor.

---

### Post by Arrgoss on 2008-12-15
3rdalbum, logging off and back on did not solve it, I already tried even rebooting.

Mads_7, adding the network monitor didn't help, either. I think the wifi icon is indeed part of the notification area, that's why is surprising it disappeared.

---

### Post by orlox on 2008-12-15
There is a bug on launchpad about this:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/43379]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/43379")

Here someone posts a workaround, but dunno if it actually works:

```

sudo killall wpa_supplicant
sudo /etc/dbus-1/event.d/25NetworkManager restart

```

---

### Post by Arrgoss on 2008-12-15
Thanks for the link, orlox. I tried, but it didn't work. Nor rebooting... I don't know what else to do.

---

### Post by Arrgoss on 2008-12-15
For some reason now it works after a reboot... So I guess the problem is solved.

---

