---
title: "kfce panel lock"
date: 2013-01-11
forum: Desktop Environments
---

### Post by Charles-2007 on 2013-01-11
I am attempting to lock a simple panel for a generic (non sudoer) user in Kubuntu 12.04.  I have a more complex panel for an admin (sudoer) user.  The kioskrc method in the howto section of the xfce site is out of date and no longer works.

Going to lightdm.conf and editing the intro to say

< channel name="xfce4-panel" version="1.0" locked="*" unlocked="root"> 

doesn't seem to work (and I separately also attempted @groupname in there too).

I restored lightdm.conf to default and then I copied 

~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

/etc/xdg/xfce4/xfconf/xfce-perchannel-xml/

but this is giving me an earlier version of panels.

I'm doing something wrong -- any help?

---

### Post by Charles-2007 on 2013-02-06
SOLVED.

[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)

---

