---
title: "[SOLVED] xfce desktop arrangement (aesthetic) randomly changed"
date: 2008-12-23
forum: Desktop Environments
---

### Post by lamikins on 2008-12-23
Hallo!
I realise this is a primarily aesthetic problem, but it's rather perplexing...  I was playing around with configuring MTA sendmail stuff and reformatting an **external** harddrive to clear it out, and when I rebooted to confirm everything was working cleanly - two things:  

[INDENT]- at my GUI login screen there is no longer a collection of graphical reboot, shutdown, logout type buttons at the bottom left corner[/INDENT]
[INDENT]- the top panel on my desktop has been completely reorganised...  "Applications" is now "xfce" with the mousewheel logo, and my clock has shifted (along with everything else) to the top left corner[/INDENT]

I realise these changes are superficial and easily stitched up manually (I will have to puddle through and alter all settings to their original state), but was wondering if this behaviour is particularly anomalous and if this problem has an easy fix or explanation?

---

### Post by lamikins on 2008-12-27
Problem solved - remove all files under ~/.config/xfce4/panel and xfce seems to rebuild the directory to defaults on reboot.

Yay!

---

