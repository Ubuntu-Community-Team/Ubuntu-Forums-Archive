---
title: "Could not set screen brightness in Dell laptop"
date: 2012-05-22
forum: Desktop Environments
---

### Post by adit on 2012-05-22
My Dell laptop always boots with 100% brightness.  In "Brightness and Lock" I adjust the level of brightness.  But after reboot gnome completely forgets my settings and sets the brightness to 100%

---

### Post by adit on 2012-05-23
BUMP
Anybody having similar problems with a Dell laptop?

---

### Post by eleftg on 2012-05-23
Yes, I have a HP dv6-6b19ev laptop and the screen brightness cannot be configured at all. Stuck at 100% no matter what I do. I learned to live with it (wearing sunglasses :-) )

Running Ubuntu 12.04 LTS

---

### Post by vigneshm247 on 2012-05-26
Hi all, 

I'm using Ubuntu 12.04 with Samsung NP300 E5z laptop. 

This really is an issue with the brightness settings. 

Every time the screen locks or the system starts the brightness goes to 100%. 

Guys please fix this .

---

### Post by vigneshm247 on 2012-05-26
Fix for this is 

[http://ubuntuforums.org/showthread.php?t=1907928&page=5](http://ubuntuforums.org/showthread.php?t=1907928&page=5)


:guitar::lolflag:

---

### Post by Toz on 2012-05-26
@adit, @eleftg, @vigneshm247:

The first thing to try would be various kernel parameters specific to brighntess controls. See [COLOR="Red"][this post]("http://ubuntuforums.org/showpost.php?p=11965133&postcount=7")[/COLOR] for information on how to do this.

If that does not work, the results of the following commands would be helpful:
[LIST=1]
[*]```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
[*]```
cat /proc/cmdline
```
[*]```
sudo lspci -vnn | grep -A10 VGA
```
[*]```
lsmod
```
[*]```
sudo dmidecode -s system-manufacturer && sudo dmidecode -s system-product-name
```
[/LIST]

---

### Post by markbl on 2012-05-27
Something changed around the 11.04 release where I found ubuntu did not handle brightness properly for my Dell laptop. I updated the bios and it has been fine since.

---

