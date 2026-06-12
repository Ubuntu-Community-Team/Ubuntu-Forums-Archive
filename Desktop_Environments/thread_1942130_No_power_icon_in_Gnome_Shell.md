---
title: "No power icon in Gnome Shell"
date: 2012-03-16
forum: Desktop Environments
---

### Post by rhaces on 2012-03-16
Hi guys,

I've been running Ubuntu 11.10 and gnome shell since its official release (I used to be in Ubuntu 10.04 for a long time) and works good, but since sime some days ago (I really don't know exactly when) I realized that the power icon is not showing anymore (not when my laptop is plugged, unplugged, charged or any) and don't seem to find out where to correct this or even why it changed.

I've looked around and haven't found the way to correct this, one of the main things I've seen is that the "icon-policy" in the org.gnome.power-manager key does not exist and I can't set is value (I want present cause I want it always to be shown). See bellow:

```
~$ gsettings set org.gnome.power-manager icon-policy 'present'
No such key 'icon-policy'
~$ gsettings list-keys org.gnome.power-manager
info-history-graph-points
info-history-graph-smooth
info-history-time
info-history-type
info-last-device
info-page-number
info-stats-graph-points
info-stats-graph-smooth
info-stats-type

```

Any help is appreciated.
Thanks,
Rodrigo

---

### Post by raja.genupula on 2012-03-17
[http://ubuntuforums.org/showthread.php?t=1804681](http://ubuntuforums.org/showthread.php?t=1804681)

---

### Post by rhaces on 2012-03-17
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=1804681](http://ubuntuforums.org/showthread.php?t=1804681)

Thanks but that doesn't help at all, as you can see it's an old thread and the main solutions were 1) a simple update and 2) to set as present the org.gnome.power-manager icon-policy but as I say in the original post, that key is not valid anymore.

---

### Post by Frogs Hair on 2012-03-17
Sorry I thought you Meant power off not power manager .

---

### Post by timefantom on 2012-03-19
I have the same issue. It finally ticked me off enough to investigate and I have discovered what you have.

There is a note in the changelog that they have dropped the panel icon somewhere in 3.2.x. I don't know why. Might have to download source package and recompile adding in the appropriate options.

It's annoying. I am hoping this issue will be fixed for 12.04. After playing with unity and gnome-Shell, in general have found gnome-shell more to my liking. :-)

---

### Post by rhaces on 2012-03-20
Well, after playing around with my extensions it looks like the "system-monitor" extension is the source of the problem, if I turn that off I can see the power/battery icon, but when on it is hidden.

Looking at the properties of the system-monitor extension there is a "Hide System Icon" checkbox.. duuuhhhh... well, that made the trick, now it is working again. I guess in a lately upgrade of that extension they added the Battery option

---

