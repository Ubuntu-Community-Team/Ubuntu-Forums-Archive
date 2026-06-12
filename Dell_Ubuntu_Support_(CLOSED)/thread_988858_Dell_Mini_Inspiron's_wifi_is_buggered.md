---
title: "Dell Mini Inspiron's wifi is buggered"
date: 2008-11-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zmjjmz on 2008-11-20
So I had to reboot it because it failed to suspend correctly (after two weeks of uptime, no less) and I woke it up to find wifi not working at all.
So after a bit of frustration, I found that for some reason the wl module hadn't been loaded so I did a ```
sudo modprobe wl
```
Now the wifi is listed in iwconfig as eth1 (as it should be), and NetworkManager can scan the networks in the area perfectly fine, but whenever I try to connect (using nm-applet) it will try for a bit, and then stop trying after a second or two.
I looked at the terminal output from nm-applet, and I see this
```
** Message: <info> Forcing device '/org/freedesktop/NetworkManager/Devices/eth1'
```

It's a bcm4310 USB controller, just so you know.

---

### Post by armandh on 2008-11-20
Ive had no problem with mine but there are different wifi guts for different countries.

---

### Post by zmjjmz on 2008-11-20
> **armandh said:**
> Ive had no problem with mine but there are different wifi guts for different countries.

Same country as you :)

It had been working fine for a good while, but after a reboot it just buggered up.

---

### Post by zmjjmz on 2008-11-22
Bump, I need this working before Monday, today would be hopeful.

---

### Post by yakker.yak on 2008-11-22
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=975498")?

Sounded like a case of a disappearing driver ...

---

### Post by zmjjmz on 2008-11-22
I'll try installing the updates and rebooting.
EDIT:
... Okay.
No updates. So what's the path for the hardware driver tool? I'm not using GNOME so I can't just find it.
EDIT2: It's jockey-gtk

---

### Post by zmjjmz on 2008-11-23
Ok, no updates. I tried disabling the wl module and then reenabling it, after rebooting, but to no avail.

Should I try to install the b43-fwcutter package?

---

