---
title: "Startup Applications - Works with manual login, fails with automatic login"
date: 2010-11-23
forum: Desktop Environments
---

### Post by TombstoneX on 2010-11-23
Has anyone ran into a problem running Startup Applications from automatic login?

I have checked to see that it is not loading in fail-safe mode, and if i disable the automatic login it works fine. Any suggestions?


The file it is loading is located in my home directory and being executed as "sh /home/myusername/script.sh"


Preston

---

### Post by awe on 2010-11-23
Login in automatically will not unlock your keyring. I wonder if this can cause this sympton. A workaround is to change the password to your keyring to blank (I mean null string, no password), and see if it works. This is a security issue, but then, in most environments it's no conern, really. If it does not help you can always set that password back to its former value. Regards.

---

### Post by TombstoneX on 2010-11-23
> **awe said:**
> Login in automatically will not unlock your keyring. I wonder if this can cause this sympton. A workaround is to change the password to your keyring to blank (I mean null string, no password), and see if it works. This is a security issue, but then, in most environments it's no conern, really. If it does not help you can always set that password back to its former value. Regards.

Thanks for the suggestion but it didn't work. I got to thinking about it this morning, and with my new awareness/ lack of sleep deprivation, i realized what the problem could be. The Gui at the point of the login is already loaded, but when i automatically login the gui is still in the process of loading. I made my script sleep for 30 seconds before issuing the commands dealing with graphical interfaces. Then BAM.... everything is working. Ill just play with the time for it to sleep before loading and it should work fine.

---

### Post by tobiz on 2011-01-25
I've found the same problem with a python script I want to run at startup.  The script unmounts and shuts down my USB backup drive if it's not the backup day (to save energy and noise).  From boot the script doesn't (seem to) run but if I logout and back in it does.  I don't want to put a delay in the script, as TomestoneX did.  Any other suggestions?

---

### Post by Krytarik on 2011-01-26
@tobiz: How about running it from "/etc/rc.local" instead?

---

