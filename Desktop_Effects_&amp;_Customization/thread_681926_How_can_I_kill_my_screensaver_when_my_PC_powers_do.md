---
title: "How can I kill my screensaver when my PC powers down the monitor?"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by Crinos512 on 2008-01-29
I have a very intensive screensaver that looks great, but sucks up lots of CPU... after about 10 minutes the monitor gets powered down to save electricity... but the screensaver is still going full blast!

If I move the mouse I see the remains of the screensaver as it dies, and can watch as my CPU usage drops back down to normal, but the whole time the monitor is off I'm wasting precious watts and heatin up my room!

Is it possible to kill my screensaver when my PC powers down the monitor? ... at that point it's not needed anymore.  :confused:

---

### Post by Crinos512 on 2008-01-30
So I take it that means you can't get there from here?

D'oh!

---

### Post by spdaniel91 on 2008-01-30
Um, Ubuntu has no way to know if your monitor is off i think. (Correct me if I'm wrong)

---

### Post by Crinos512 on 2008-01-30
is there a way to kill the screensaver after a certian duration? in such a way that if I come back and move the mouse the screensaver can start back up.

---

### Post by FuturePilot on 2008-01-30
The screensaver stops when the monitor turns off. The reason you see a little bit of it when your monitor comes back on is because it's trying to start it again. You can see this if you open Gnome System Monitor and go to the Processes tab. Leave it there until the screensaver comes on and then the monitor turns off. Wait about a minute after it turns off, then wake it up and you'll see your CPU dropped off after the monitor turned off.

---

### Post by Crinos512 on 2008-01-30
well if I let the screen saver blank out and go to powersave mode then wait a wile when I move the mouse I see my CPU is really hot and my CPU Usage history is close to maxxed out ... up to the point I move the mouse.

Found this on the [xsreensaver FAQ]("http://www.jwz.org/xscreensaver/faq.html#dpms-load")
> **The manual says that xscreensaver will stop running graphics demos when my monitor goes into power-saving mode, but it doesn't. Why?**

The only way that xscreensaver can tell that the monitor is in power-saving mode is by asking the X server. There is a server extension specifically for asking these sorts of questions, called "XDPMS", and xscreensaver uses that. 

So it may be that your X server doesn't support the XDPMS extension (you can tell by running "xdpyinfo"). Or, it may be that the extension is supported, but the X server doesn't actually know how to talk to your hardware to ask it whether it is powered on or off. The latter is especially likely on laptops: many laptops have monitor power-saving behavior built in at a very low level that is invisible to Unix and X. On such systems, you can typically only adjust the power-saving delays by changing settings in the BIOS in some hardware-specific way. 

If the Power Management settings in the Preferences panel are grayed out, then that means that either: xscreensaver was compiled without DPMS support; or xscreensaver believes that your system does not support power management.

---

### Post by FuturePilot on 2008-01-30
Check to see if you have 
```
 Option          "DPMS"
```
under the Monitor section in xorg.conf. If you don't try adding it.
Log out and then back in if you end up adding it.

---

