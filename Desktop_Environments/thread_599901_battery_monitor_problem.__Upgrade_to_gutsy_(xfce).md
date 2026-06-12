---
title: "battery monitor problem.  Upgrade to gutsy (xfce)"
date: 2007-11-01
forum: Desktop Environments
---

### Post by Alpha_Maverick on 2007-11-01
I am using a Gateway solo3350.  All installations are xUbuntu.

I had Feisty and the battery monitor worked great.  I upgraded (fresh install) to Gutsy and tried to get the battery monitor on the panel.  The battery monitor applet shows up in the panel, but it says battery is 0.00% and is on A/C power, no matter what it's true state is.  ```
acpi -V
``` returns:```
Thermal 1: ok, 50.0 degrees C
AC Adapter 1: on-line
```no matter what the actual condition is.

edit: I have 3 of these laptops, and only one had been upgraded.  I ran the same tests on the others, and they returned much more appropriate results.  It is definitely in the upgrade, and looks similar to something that happened in a kernel upgrade quite a while ago.  does anyone have a fix for this kernel?
/edit

I have searched, but I have been unable to find anything on this.  I really need to know how much power I have left.

Thanks in advance,

Mav

---

### Post by Alpha_Maverick on 2007-11-02
update:

I tried to reinstall, and when the live cd was booting up, I got the following string of messages:
```

(...)
*Configuring network interfaces...
cat: /var/lib/acpi-support/system-manufacturer: no such file or directory
cat: /var/lib/acpi-support/system-product-name: no such file or directory
cat: /var/lib/acpi-support/system-version: no such file or directory
cat: /var/lib/acpi-support/bios-version: no such file or directory
*Saving VESA state...
(...)

```
Is there any way to fix this?

BTW, is this in the right forum? if not, mods please move it to the appropriate area.

edit:
I put the 7.04 disc in and it had the same series of messages, despite the fact that the battery monitor and "acpi -V" shows correct values
/edit

edit2:
under 7.10 I just tried "acpi -s" and it returned "Battery 1: slot empty"
I checked the acpi versions between 7.04 & 7.10 and they are the same
/edit

---

### Post by Alpha_Maverick on 2007-11-04
I have checked all things that *might* influence the battery monitor, and it seems that the only option would be that the kernel is messed up/missing something.  Any input/links to how to downgrade the kernel would be appreciated.

Until then, since no one else seems to have the same problem, or care, I will probably be switching back to 7.04.  Most disappointing, since I see many other improvements in 7.10, but I need to have access to the battery monitor.

---

### Post by googlenator on 2007-11-04
I am having the same problem about it. I still haven't had it working yet. Any ideas to fix it?

---

### Post by Alpha_Maverick on 2007-11-05
I have found the following threads which are applicable to an older kernel, but I am trying to figure out an equivalent solution for this kernel.

[http://ubuntuforums.org/showthread.php?t=516533&highlight=battery+applet+kernel](http://ubuntuforums.org/showthread.php?t=516533&highlight=battery+applet+kernel)
[http://ubuntuforums.org/showthread.php?t=461272&highlight=battery+applet+kernel](http://ubuntuforums.org/showthread.php?t=461272&highlight=battery+applet+kernel)

any developer/admin input would be great

edit:
apparently, this IS the same bug, and it can be found here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773)

I am going to try to get the older kernel support to work. wish me luck!
/edit

---

### Post by Alpha_Maverick on 2007-11-17
after the recent updates, no change.  ACPI is still acting screwy.  Can anybody help?

---

