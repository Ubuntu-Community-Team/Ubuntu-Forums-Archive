---
title: "Blinking wifi light on Dell e1505 using wicd"
date: 2009-04-05
forum: General Help
---

### Post by xg7 on 2009-04-05
I've tried all the fixes, and I was able to remedy this problem using one when I was using Network Manager.  However, I switched to wicd for a reason and would like to stick with it.  I've tried every blinking light fix I could find on the forum to no avail.  Please help :)

---

### Post by xg7 on 2009-04-06
Thanks

---

### Post by MikeFlint on 2010-11-01
Did you ever get this solved?

I have just put the standard pipe command to kill the LEDs into a shell script and added that script into the WICD script area for the access point I use.  Seems to work (fingers crossed).

---

### Post by MikeFlint on 2010-11-10
Okay ... updating on that.

Due to problems with speed drops on WiFi (for no discernible reason), I did the usual, drop n-m for wicd, killed off IPv6 in the boot, but nothing worked.

So I eventually built a later iwl3945 driver from the downloads available [here]("http://linuxwireless.org/download/compat-wireless-2.6/")

(this seems to be a bit hit-and-miss; if you build one and it wont load, then keep going older until one works ... they are all 2010 so not that 'old')

and this seemingly has cured the speed problems.  However, it also no longer created the led streams in the place they were, or anywhere I could find them.

So, the "kill the LED" solution I now use is:

modinfo iwl3945  (nope - nothing there)
modinfo iwlcore  (ah-ha ... led_mode 0 - default means 'blink', but 1 means always on or always off ... super!)

Okay, create a file in /etc/modprobe.d with a "options iwlcore led_mode=1" line in it.
Take the module down (modprobe -r iwl395) ... not iwlcore as it is depended upon by iwl3945.
Bring it back up again, 'modprobe iwl3945', and that light no longer blinks!

Hopefully that's the end of it.

---

