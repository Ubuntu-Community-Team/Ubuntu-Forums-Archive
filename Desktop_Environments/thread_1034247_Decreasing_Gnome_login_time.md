---
title: "Decreasing Gnome login time"
date: 2009-01-08
forum: Desktop Environments
---

### Post by blazemore on 2009-01-08
Is there a way to speed up the process from GDM login screen, to fully functional desktop?
With XFCE, and the same startup apps, it starts up much quicker.

Any ideas?

---

### Post by blazemore on 2009-01-08
*bump* tiem

---

### Post by ingegnerlillo on 2009-01-08
> **blazemore said:**
> *bump* tiem

For me, removing any desktop effects at login works very well...

---

### Post by MighMoS on 2009-01-08
If you've got RAM to spare, preload works great. ```
sudo apt-get install preload
```

Also, you can disable some items in Preferences-->Sessions if you feel you wont ever need them.

---

### Post by oldos2er on 2009-01-08
Autologin.

---

### Post by adamlau on 2009-01-09
Nothing. Really. You can do all you want, lose compositing, disable everything you can possibly disable and Xfce with GNOME services launched at startup will always be faster (LXDE and others, faster still) upon login. Running 8.10 + GNOME off 4GB (2.7GB detected), P4 3.0 and an Mtron 7500 SSD on XFS (noatime, -l size=64m,lazy-count=1) with logdev to a third-gen VelociRaptor will still result in mouse cursor spin upon login (and noticeable latency on the same system versus Xfce). Bottom line: Stick with Xfce if GNOME login time and overall resource consumption bother you to that extreme. It bothers me, so I prefer Xfce over GNOME across any and all distros.

---

### Post by blazemore on 2009-01-09
I'm wondering, could you use XFCE with:
Gnome-panel
Nautilus
Metacity

So essentially you'd be running Gnome, since XFCE uses GTK?
Would this be faster than Gnome?
I've got my boottime down to 19s, so this lag at login is really noticable.

---

### Post by adamlau on 2009-01-09
I have not tried that combo and am unsure about integration, though I do not see why you would use Nautilus over Thunar. Search is the only useful feature lacking in Thunar, but that is easily remedied with a UCA. In fact, many users transition to Xfce in an attempt to move away from Nautilus. If you really want the look and feel of GNOME, then I suggest you take a look at Xfce 4.6 Hopper. It still needs work, but is stable enough for me to use on my secondary PC :) .

---

### Post by Tomatz on 2009-01-09
If you have a dual core cpu, this will speed up the boot process:

```
sudo gedit /etc/init.d/rc
```

find the line ***CONCURRENCY=none*** and change it to: ***CONCURRENCY=shell***

Reboot to see the changes.


More here:

[http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast](http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast)

---

### Post by adamlau on 2009-01-09
What you can do to improve the responsiveness of GNOME is to compile its source packages with unnecessary (to you) features removed and compiler optimizations flagged and installing from there. For example, I am running Ubuntu Minimal + XFCE 4.4.3. I compiled and installed the latest Thunar from SVN (0.9.92svn-29116) with minimal options. The result? A noticeable difference in Thunar startup and directory load times.

---

