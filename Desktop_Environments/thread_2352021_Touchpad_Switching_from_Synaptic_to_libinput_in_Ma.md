---
title: "Touchpad: Switching from Synaptic to libinput in Mate 16.04"
date: 2017-02-08
forum: Desktop Environments
---

### Post by mike-g2 on 2017-02-08
I'm running Ubuntu Mate 16.04 on a Yoga 2 thinkpad.  The touchpad performs poorly and I'd read that many of these problems can be solved by switching from using synaptic to libinput.  I've installed libinput, but synaptic is still being used.  I've tried changing the number of the .conf files in /usr/share/X11/xorg.conf.d so that libinput has a lower number than synaptic, but that didn't have any effect.  Can someone clue me in to

a) Whether or not libinput is supported in UbuntuMate
b) How to implement it if so.

---

### Post by mc4man on 2017-02-09
a. - no clue
b. - remove xserver-xorg-input-synaptics package, if installed it will be used.

---

### Post by mike-g2 on 2017-02-10
Unfortunately removal does not seem to be an options
```
$ sudo dpkg -r xserver-xorg-input-synaptics 
dpkg: dependency problems prevent removal of xserver-xorg-input-synaptics:
 xserver-xorg-input-all depends on xserver-xorg-input-synaptics.

dpkg: error processing package xserver-xorg-input-synaptics (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 xserver-xorg-input-synaptics

```
Of course, now that I've tried to remove synaptics its behavior has gotten worse.

---

### Post by mike-g2 on 2017-02-10
Update: So feeling reckless I tried,
```
 sudo dpkg -r --force-depends xserver-xorg-input-synaptics 

```
and then rebooted.

Nothing seems to be broken and the touchpad seems to work.

Yippie

---

### Post by mc4man on 2017-02-11
Yeah, I typically use synaptic package manager which would happily remove both. 
The  xserver-xorg-input-all package is a meta package, i.e. it only has dependencies (4) & doesn't actually provide anything so it's quite safe to remove.

---

### Post by mike-g2 on 2017-02-12
Update: My solution was only a partial solution because when I go to install a package using apt the program wants to reinstall the xserver-xorg-input-synaptics package.

My workaround was to (a) replace the input-synaptics package with a custom created dummy package with the same name by following the instructions from [http://askubuntu.com/a/626912](http://askubuntu.com/a/626912) and then lock this package to its current release in the synaptic package manager.

I'm not convinced this is a complete solution because now my caps_lock has reverted from acting as a ctl key to caps_lock again.  Sigh.

---

