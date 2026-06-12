---
title: "Dual Boot time issues"
date: 2005-07-14
forum: Desktop Environments
---

### Post by zerhacke on 2005-07-14
I am dual booting Hoary 5.04 and Windows XP Professional.

Every time I reboot from Linux to Windows, the time is off by 4 hours on the Windows machine.

I suspect it has to do with the Linux time, since when I am not connected to the internet and cannot synchronize with the NTP server and then reboot to Windows the time is not off.

How can I set my time so that it is correct for both Windows and Linux without having to resynchronize every time I reboot?

---

### Post by badrinarayan on 2005-07-14
Open a command prompt. Type [FONT=Courier New]sudo gedit /etc/default/rcS[/FONT]
Change **UTC=yes** to **UTC=no**
Save the file and close the editor
Type **sudo /etc/init.d/ntpdate restart**
(edited typo)

Regards
Badri

---

### Post by zerhacke on 2005-07-14
[QUOTE=badrinarayan]Open a command prompt. Type [FONT=Courier New]sudo gedit /etc/default/rcS[/FONT]
Change **UTC=yes** to **UTC=no**
Save the file and close the editor
Type [FONT=Courier New]sudo /etc/init/ntpdate restart[/FONT]

Regards
Badri[/QUOTE]
sudo /etc/init/ntpdate restart gives me a command not found error.

---

### Post by badrinarayan on 2005-07-14
Sorry make it [FONT=Courier New]sudo /etc/init.d/ntpdate restart[/FONT]

Regards
Badri

---

### Post by zerhacke on 2005-07-14
That worked, now it's time to restart and find out if Windows time is ok.

*edit added

Yep, time is fine now on both operating systems.

---

