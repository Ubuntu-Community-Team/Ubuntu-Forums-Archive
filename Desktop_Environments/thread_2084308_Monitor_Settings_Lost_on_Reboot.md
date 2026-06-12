---
title: "Monitor Settings Lost on Reboot"
date: 2012-11-15
forum: Desktop Environments
---

### Post by jakfish on 2012-11-15
Lubuntu 12.04 on Lenovo S10-3t.  Installed on a 6GB ssd partition; the rest of the ssd is for Windows 7 Premium.

Not using a screensaver, I can't get Lubuntu to remember my monitor blanking settings in /Preferences/Power Manager/On AC/Monitor

I set "Put display to sleep when computer is inactive for:" 2 minutes.

I set "Switch off display when computer is inactive for:" 3 minutes

In "Extended" I have set everything to "suspend"

I have set the same for /Preferences/Power Manager/On Battery/Monitor

These settings all work, but they aren't remembered upon reboot, and I have to set them all again.

Any ideas why this is happening?

And is it possible to make these setting in console, as a command, so I could run a script in Autostart?

Many thanks for all help,
Jake

---

### Post by jakfish on 2012-11-15
[http://ubuntuforums.org/showthread.php?t=1957774](http://ubuntuforums.org/showthread.php?t=1957774)

A helpful thread, which appears to give a workaround.

In /home/user/.bashrc, I put this command at the end of the file:

xset dpms 0 120 180

So far, this establishes permanent settings, overriding any problems I'm finding in Power Manager.

Jake

---

