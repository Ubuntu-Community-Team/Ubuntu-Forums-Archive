---
title: "Which daemon does nm-applet invoke?"
date: 2009-06-02
forum: Desktop Environments
---

### Post by pwuerrer on 2009-06-02
Hi all.
I want to stay minimalistic, so I built dwm from source.
Everything works fine except one thing: If I want to use my wireless (broadcom), I must first log into gnome, then logout, and then into dwm, else it won't work.
I suspect nm-applet is responsible for wireless, so I want to know which networking daemon it invokes.
I tried wpa_supplicant -dwext -ieth1 -Cup but unfortunately this doesn't work.

---

### Post by regala on 2009-06-02
> **pwuerrer said:**
> Hi all.
I want to stay minimalistic, so I built dwm from source.
Everything works fine except one thing: If I want to use my wireless (broadcom), I must first log into gnome, then logout, and then into dwm, else it won't work.
I suspect nm-applet is responsible for wireless, so I want to know which networking daemon it invokes.
I tried wpa_supplicant -dwext -ieth1 -Cup but unfortunately this doesn't work.

it invokes NetworkManager, which in turn launches wpa_supplicant in daemon mode. If something is changed in nm-applet configuration, or in network topology, NetworkManager invokes dbus to talk to wpa_supplicant, and tell it to change its configuration subsequently. Do you have a systray in dwm ? If so, you can execute nm-applet, it should appear in it, and can run independently of gnome. You can also try wicd, which is another system-wide network daemon, with systray integration.

br, mathieu

---

### Post by pwuerrer on 2009-06-02
unfortunately I don't have any system tray in dwm.
how would the configuration for wpa_supplicant look, if I have a broadcom bcm 4312 wireless, use the restricted broadcom sta drivers and want it to connect to the unsecured network WUNET?

---

### Post by regala on 2009-06-02
> **pwuerrer said:**
> unfortunately I don't have any system tray in dwm.
how would the configuration for wpa_supplicant look, if I have a broadcom bcm 4312 wireless, use the restricted broadcom sta drivers and want it to connect to the unsecured network WUNET?

thru Google, search for "wpa + supplicant + configuration + example" gave me:
[http://linux.byexamples.com/archives/148/setting-wpa-supplicant-for-wifi-access/](http://linux.byexamples.com/archives/148/setting-wpa-supplicant-for-wifi-access/)

but, if you go that way, you may have to deinstall or at least disable NetworkManager.

---

