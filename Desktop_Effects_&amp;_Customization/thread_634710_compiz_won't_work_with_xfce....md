---
title: "compiz won't work with xfce..."
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by afallucco on 2007-12-08
When I go to run comiz from the terminal I get this error message.

anthony@anthony-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200020 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

Anyone know how to fix this...

---

### Post by santiagoward2000 on 2007-12-08
> **afallucco said:**
> When I go to run comiz from the terminal I get this error message.

anthony@anthony-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200020 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

Anyone know how to fix this...

Hi!
Could you tell us what video card are you using?

---

### Post by afallucco on 2007-12-08
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)

straight from the terminal....

---

### Post by afallucco on 2007-12-08
bump

---

### Post by santiagoward2000 on 2007-12-09
Hi!
Sorry for the delay, I was trying to get some info on your card. I'm not familiar with it, but it seems it needs XGL to run Compiz. You can either install it through Synaptic (the package is called **xserver-xgl**) or by typing on a Terminal:
```
sudo apt-get install xserver-xgl
```
If you are using Gusty that should so it after a reboot.
If you are on Feisty, Edgy, etc, you should follow this guide to get it working:
[http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m")

I hope this helps!

---

