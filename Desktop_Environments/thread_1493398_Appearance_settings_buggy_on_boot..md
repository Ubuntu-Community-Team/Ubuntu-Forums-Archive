---
title: "Appearance settings buggy on boot."
date: 2010-05-25
forum: Desktop Environments
---

### Post by tekonus on 2010-05-25
Hi! This is my first post, as this bug is the reason I signed up to the forums in the first place. Sorry if I sound a bit noobish. :P

Here is a description of my problem:
I am running Ubuntu 10.04 on my desktop with the default Ambiance theme. I have my bottom panel deleted and instead use Docky.
Sometimes on boot/reboot one of a few things happens.

Either:
**1)**My Ambiance theme loads, then... unloads? My top panel and all Nautilus windows turn to a flat gray "theme" as if I guess there are no appearance settings enabled. If I open appearance settings my panel returns to theme without doing anything else, but my Nautilus windows are still out of theme.
**2)**My Docky bar never loads up and I have to start it manually, it then loads/works fine as if nothing is wrong.
**3)**Both problems 1 & 2 combined.

My setup is Ubuntu 10.04 64bit running on an Athlon x2 3.0GHz with 8gig of DDR2 dual channel RAM and a Geforce 9800GTX+ video card. I had the latest factory NVidia driver installed and figured that might be causing the problem. I switched an older release of the NVidia driver last night to see if that fixes anything, but being an intermittent problem only a few days use will tell. I would not use the NVidia drivers at all, but I figured I would not be able to use Docky as it requires compositing to be enabled (which I was under the assumption were under the special effects that I need the NVidia driver for).

If I am missing something silly a point in the right direction would be appreciated. I am very curious if anyone else is having this problem as I've googled my heart out and found nothing about this.

---

### Post by nacho-wan on 2011-01-05
Welcome aboard the randomess decoration wagon. I'm having the same issue since Lucid - I actually upgraded last weekend to Maverick to see if I could forget about this issue. However no luck. I'm running Ubuntu 32bits on Dell Inspiron 1525 with Intel Dual Core

---

### Post by johnfkennady on 2011-01-05
waiting for solution too    ):P

---

### Post by stinkeye on 2011-01-05
Quick fix...
```
gnome-settings-daemon && killall nautilus
```



> I figured I would not be able to use Docky as it requires compositing to be enabled (which I was under the assumption were under the special effects that I need the NVidia driver for
You can enable compositing for Metacity.
Alt+F2 and run...
```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true
```

---

