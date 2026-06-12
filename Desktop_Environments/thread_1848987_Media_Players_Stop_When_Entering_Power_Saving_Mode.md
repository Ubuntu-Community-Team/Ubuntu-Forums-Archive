---
title: "Media Players Stop When Entering Power Saving Mode"
date: 2011-09-23
forum: Desktop Environments
---

### Post by Prism on 2011-09-23
Hi there,

Lately I started using KDE 4. I discovered that when my computer enters power saving mode (meaning turning off the display), all my media players actually stop - that includes Amarok, Clementine etc.

It's important to say that I'm a desktop user, not a laptop. In my Power Management settings (in the KDE System Settings), only the "Screen Energy Saving" option is selected.

My guess is that Phonon interprets the power saving mode as "shut up" command - and it's quite annoying.

Anybody has a clue?
Thanks in advance!

---

### Post by schnelle on 2011-09-24
I had a similar problem in Kubuntu Natty while I used opensource ati drivers. I asked for help in many linux forums but I found no help. Then I installed catalyst driver and I am not having problems anymore.

---

### Post by rat_poison on 2011-11-02
Being an ATI Radeon x1950 user I have no Catalyst support and therefore still face the problem. Any solution for people with older ati/amd hardware?

---

### Post by schnelle on 2011-11-02
> **rat_poison said:**
> Being an ATI Radeon x1950 user I have no Catalyst support and therefore still face the problem. Any solution for people with older ati/amd hardware?

When I don't use catalyst my workaround is to set "dim display" and "screen energy saving" to 360min.

---

### Post by schnelle on 2011-11-16
Another workaround is to use xfce4-power-manager instead of default powerdevil. With xfce4-power-manager players don't stop playing while monitor is off (but then suspend to ram doesn't work).

I am going to file bug report to bugs.kde.org about this.

---

### Post by schnelle on 2011-11-25
Bug report: [https://bugs.kde.org/show_bug.cgi?id=287580](https://bugs.kde.org/show_bug.cgi?id=287580)

---

### Post by schnelle on 2012-06-08
This is bug in opensource radeon driver and it is fixed now:
[https://bugs.freedesktop.org/show_bug.cgi?id=49761](https://bugs.freedesktop.org/show_bug.cgi?id=49761)

If you are using Kubuntu 12.04 you can install newest (fixed) drivers from oibaf ppa:

```
sudo apt-add-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get dist-upgrade
```

and then reboot your system.

---

### Post by whatthefunk on 2012-06-08
Run "xset -q" in a terminal to see if DPMS is enabled.  In a lot of Kubuntu installs, DPMS turns on whenever it wants, so if its on do "xset -dpms"

---

