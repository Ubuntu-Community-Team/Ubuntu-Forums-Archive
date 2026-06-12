---
title: "Help Shutting Down!"
date: 2005-07-29
forum: Desktop Environments
---

### Post by leslie on 2005-07-29
Cannot shutdown!

Ubuntu works great on my laptop install reasonably well and after removing the batstat-applet-2 everything works like a dream. 

Expect when it comes to shutting the thing down!!! When I choose system -> log off -> shutdown or log off and shutdown from the login screen the process always hangs.

System output is as follows:
---
System is shutting down, please wait 
---

* Switching to run level: 0
* Sending processes the TERM signal
* Stopping GNOME Display Manager…
* GNOME Display manager not running                    [ok]
* Stopping periodic command scheduler…                [fail]
* Stopping Common Unix Printing System: cupsd     [ok]
* Disabling Power Management…


That’s it! It just hangs with a flashing cursor.

Why does “Stopping periodic command scheduler…” fail and why does it just hang when trying to “Disabling Power Management…”

 I just have to remove the battery from the laptop to turn the dam thing off. 

Any help will be greatly appreciated.  ](*,)

---

### Post by fimbulvetr on 2005-07-29
Can you shut down power management while your laptop is running normally? 
How about trying to shut it down, confirming it is shutdown, then powering off? Does that work correctly?

---

### Post by leslie on 2005-07-30
Please tell me how whould i do that?

---

### Post by david on 2005-07-30
Hi,

i had a similiar problem when I installed Ubuntu on an old laptop,
it wouldn't shut down properly. The fix for me was to change from ACPI to APM power management.

Here's a thread on how to change to APM 
[http://ubuntuforums.org/showthread.php?t=30337&highlight=apm](http://ubuntuforums.org/showthread.php?t=30337&highlight=apm)

---

### Post by GavinX on 2005-07-30
An easy fix:

1. In a terminal type 'sudo gedit /boot/grub/menu.lst' (without the ")
2. Look for the line which begins with "kernel......." (please note, not one of the lines which begins with a '#' this is called a comment and it will not work)
3. at the end of the line add 'acpi=off' (again without the ")
4. Reboot then shutdown and all should be well
5. If you shutdown and nothing still happens, follow all the steps again but this time use 'acpi=force' in step 3.

---

### Post by simonjardine on 2005-08-04
i use lilo, i looked in /etc/lilo.conf, As i am using lilo, i also have the same problem, my system is working great, right until i try to log out, as soon as i do, the system locks, i can still (alt ctrl f1) to a promt, then log in as root, then halt, or reboot, do you think that is a dodgy way of doing it?

Any help for me? Newbie at Linux, but loving it. ](*,)

---

