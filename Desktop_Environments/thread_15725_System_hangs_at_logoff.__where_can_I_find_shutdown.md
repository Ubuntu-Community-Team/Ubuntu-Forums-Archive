---
title: "System hangs at logoff.  where can I find shutdown logs??"
date: 2005-02-16
forum: Desktop Environments
---

### Post by puelly on 2005-02-16
Hello,

I recently installed Ubuntu and been trying to get accostumed to it.  I had compiled and installed the ndiswrapper to use my DWL-122.  Unfortunately, now when I log off the system.  It hangs.  I am not sure what's the cause of this issue and I hope that the error is being recorded somewhere.

Could this be a conflict between eth0 and wlan0?

---

### Post by az on 2005-02-16
/var/log/messages.

What is displayed on your screen as you shut down?

---

### Post by puelly on 2005-02-16
[QUOTE=azz]/var/log/messages.

What is displayed on your screen as you shut down?[/QUOTE]
 

Gnome just hangs and I am left staring at the gnome desktop with control of the mouse but I can't activate anything.  Eventually I am just forced to hard reset the pc.   I'll go check those logs now, I hope the prob is ducumented there.

Thanks.

---

### Post by puelly on 2005-02-17
I have pinpointed that the problem only occurs when I  load "modprobe ndiswrapper", the system freezes when i log off.  It hangs at the ubuntu desktop.  No indication what's causing the prob in /var/messages

Any suggestions?

---

### Post by Wim Sturkenboom on 2005-02-18
Just a possible workaround. Go to a virtual console (i.e. <ctrl><alt><F1>), login and shutdown from there.
If you did not enable a root account and have to login as a normal user:
to shutdown
*sudo shutdown -h now*
to reboot
*sudo shutdown -r now*

---

