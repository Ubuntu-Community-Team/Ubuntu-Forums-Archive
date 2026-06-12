---
title: "Compiz: Resizing Window in Normal mode causes unbelievable effects"
date: 2010-05-25
forum: Desktop Environments
---

### Post by plopp37 on 2010-05-25
I used to have Compiz set to resize my windows in Normal mode, thus seeing the contents of the window changing while resizing. Everything worked fine until Karmic and it persists in to Lucid these days...

The problem is that the area around the window that is meant to draw decorations (window borders and shadows) starts to flash with white color wildly as I start to resize, causing a strange stroboscope effect on my display — rendering the Normal window resize mode useless.

Anyone has the same problem? I didn't find anything on the web, although I've seen the same bug on my friends laptop with probably the same Intel graphics chip inside...

---

### Post by plopp37 on 2010-05-29
Am I the only one to suffer from this?

---

### Post by MariusLV on 2010-07-15
> **plopp37 said:**
> Am I the only one to suffer from this?

Nope. I have the same behavior. No idea what causes it though. However, since Compiz in Ubuntu defaults to Rectangle mode despite Normal mode being both more intuitive and more useful, I can only assume that Normal mode is known to cause problems. I too would like to see Normal mode work without graphical glitches. If only someone would file a bug report...

---

### Post by stinkeye on 2010-07-15
Works fine here on a GeForce 9400GT using 256.35 drivers.

---

### Post by pmontrasio on 2010-09-13
Same problem here on a fresh 10.4 installation.
I had no problems on the same notebook with Ubuntu 9.10. It was originally installed with 8.10 and upgraded to 9.04 and 9.10. No problems with those versions too.

The graphic card is a Radeon Mobility x1600.

Resize mode Stretch works fine on 10.4 but I like it as much as I like the flashing white border of Normal mode resize ;-)

---

### Post by pmontrasio on 2010-09-13
Problem solved with a workaround.

First, there are a couple of open bugs on this issue: you might want to vote for them. They are [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/454218](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/454218) and [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/559183](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/559183)

The solution from one of those threads is:

sudo apt-get install fusion-icon
Add /usr/bin/fusion-icon to Startup Applications or run it from command line
You'll get an icon in the notification area of your panel.
Click on it, Compiz Options, check Loose Bindings.

It seems that Compiz or something else is too slow at redrawing the border and we see the area being redrawn flashing.

---

