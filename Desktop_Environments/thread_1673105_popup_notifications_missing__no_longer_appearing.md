---
title: "popup notifications missing / no longer appearing"
date: 2011-01-21
forum: Desktop Environments
---

### Post by shinkaide on 2011-01-21
Hey guys,

Just wondering if anybody else is experiencing this: the pop-up notifications that usually appear on the top-right of the screen when I increase/decrease the volume via media keys on my laptop (among other notifications) are gone. 

Is there a way I can restore those?

---

### Post by Krytarik on 2011-01-21
Try re-installing the package "notify-osd":
```
sudo apt-get install --reinstall notify-osd
```

---

### Post by shinkaide on 2011-01-21
It works again, but only partially. I get popup notifications when I connect or disconnect to and from wired / wireless connections, but volume increase / decrease notifications are still borked. :???:

---

### Post by Krytarik on 2011-01-22
I just yet did a short web search on this, it seems that there are multiple issues regarding the display of the volume level.

Have you installed a modified version of notify-osd via PPA, or configured it somehow?
Do you have the package "notification-daemon" installed parallelly (shouldn't be)?

---

### Post by shinkaide on 2011-01-22
> Have you installed a modified version of notify-osd via PPA, or configured it somehow?
Do you have the package "notification-daemon" installed parallelly (shouldn't be)? 

Nope, nothing of the sort. Didn't tinker with anything having to do with Ubuntu's core configuration - the most I've done are really just cosmetic changes (installed theme engines, nautilus modifications, the like). Even after those, the volume notifications continued to work. It's only been a day or two since the popups disappeared, and I can't figure out why.

The package you've mentioned is also not installed.

---

### Post by shinkaide on 2011-01-24
Um... anyone?

---

### Post by stinkeye on 2011-01-24
I get this problem occasionally but after running
```
pkill notify-osd
```
it appears again.

---

### Post by shinkaide on 2011-01-24
Didn't work for me. I also tried sudo, but no such results. :|

---

### Post by thaDM on 2011-02-17
I have this problem too... ish.

My volume and brightness OSDs are fine but all others do not appear.
Haven't tried the above solutions yet as I am looking this up at work but will let you know if they work for me later.

---

### Post by thaDM on 2011-02-17
Yeah the solutions above didn't work.

---

### Post by thaDM on 2011-03-25
Mine all seem to be working now. Has there been an update?

---

