---
title: "kubuntu 9.10 fresh install on Dell 5100"
date: 2010-02-02
forum: Desktop Environments
---

### Post by VaineDragon on 2010-02-02
When KDE desktop appears the bottom menu bar is black, and when it is clicked upon it turns thready lines with multiple colors, not usable at all.

This is a Dell Inspiron 5100 with an ATI Raedon Mobility 7500 series 16 megabyte Video Adapter.

Is there a quick fix for this issue or is this laptop just another POS Dell product?

TIA
Dragon

---

### Post by rogue_0111 on 2010-02-02
To troubleshoot I would:

- do an update
- add another panel and see what happens
- try changing resolution
- check if it does this in Gnome

--

---

### Post by VaineDragon on 2010-02-02
I was able to fully update and nothing changed, how do I get GNOME up, will I need to install it first since this KDE?

---

### Post by hikui on 2010-02-03
Try the new ati driver

---

### Post by schnelle on 2010-02-03
> **VaineDragon said:**
> I was able to fully update and nothing changed, how do I get GNOME up, will I need to install it first since this KDE?

For installing gnome:
```
sudo aptitude install ubuntu-desktop
```

Then after reboot at login screen choose gnome session.

---

### Post by schnelle on 2010-02-03
You can also try with updated drivers. Add this repository to your sources.list:

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main 

Then to add key for this repository:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
```
Then update:
```
sudo aptitude update
sudo apptitude safe-upgrade
```

After updating reboot your system.

I hope this will help. I am using drivers from this repository without any problems.

---

