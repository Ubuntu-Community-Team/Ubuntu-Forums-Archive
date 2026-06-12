---
title: "GNOME won't run at startup"
date: 2010-10-09
forum: Desktop Environments
---

### Post by brazov on 2010-10-09
Hi everybody. Ubuntu 10.4.

When I boot my computer I only get the command line. By giving
```
sudo gdm
```
then I have again my desktop and all is fine.
If I press Ctrl-Alt-F1 I go back to the terminal and can read:
```
gdm-binary[1635] WARNING: Unable to find users : no seat-id found
```

Recently I had restored gnome in its original form. I cannot find the thread, maybe the command was
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```

Anyway it was working perfectly for at least one month up to some upgrade. Suddenly, GNOME does not start.

I tried to remove and reinstall gdm (maybe this is silly).

A workaround is described in update #3 [here]("http://efreedom.com/Question/3-142339/GDM-Automatically-Start-Boot").
But this is clearly a bad solution, which will probably give conflicts in the future.

In my file /etc/init/gdm.conf there is nothing such as "start on runlevel 5". There is
```
start on (filesystem
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))

```
so I suppose that the boolean condition there becomes no more satisfied.

By
```
sudo sysv-rc-conf

```
I can see that gdm has no runlevel. Setting it at level 5 has no positive consequencies.

---

### Post by mvklingeren on 2010-10-09
Have you tried this already?

sudo dpkg-reconfigure gdm

---

### Post by brazov on 2010-10-09
> **mvklingeren said:**
> Have you tried this already?

sudo dpkg-reconfigure gdm

Yes, I tried it.

---

### Post by mvklingeren on 2010-10-09
What about removing gdm, and gnome-desktop

sudo apt-get remove gdm gnome-desktop

and reinstalling them?

I know its a bit overkill, but if it costs days to try to find the problem/figure it out.. this might be a shortcut in getting it fixed.

---

### Post by brazov on 2010-10-09
Computer's answer: cannot find gnome-desktop package (the actual answer is in Italian)

I already removed and re-installed gdm.

---

### Post by brazov on 2010-10-10
I choosed a different workaround.
I removed the condition
```
and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger)
```
for the start of gdm in /etc/int/gdm.conf, and now gnome starts without any command in /etc/rc.local .

Anybody knows the meaning of the condition I removed? And what could be the consequencies?

ATI Technologies Inc Radeon HD 2400 XT

---

