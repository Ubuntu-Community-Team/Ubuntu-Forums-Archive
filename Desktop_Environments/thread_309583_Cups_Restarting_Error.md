---
title: "Cups Restarting Error"
date: 2006-11-29
forum: Desktop Environments
---

### Post by Meekajahama on 2006-11-29
Sorry if there is a thread about this already but I searched and could not find it.
While trying to install my Lexmark Z615 printer using this method: [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)
I have been fine up until this step: The driver is now installed. Restart the cups daemon:
Code:

/etc/rc2.d/S19cupsys restart

When I enter in that command I get this error:
blaine@Blaine:~$ /etc/rc2.d/S19cupsys restart
open: Permission denied
* Restarting Common Unix Printing System: cupsd start-stop-daemon: warning: failed to kill 18885: Operation not permitted
cupsd: Child exited with status 1!
blaine@Blaine:~$
Message from syslogd@Blaine at Wed Nov 29 20:10:47 2006 ...
Blaine cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting! 

Do I need cups to be restarted to finish installing the printer? Will restarting my computer help? Thanks for the help ](*,) 

I'm using Ubuntu 6.10

---

### Post by Voxxi on 2006-11-30
Try putting:

```
***sudo*** /etc/rc2.d/S19cupsys restart
```

Then, enter your password when prompted.

Should work now ;) .

---

