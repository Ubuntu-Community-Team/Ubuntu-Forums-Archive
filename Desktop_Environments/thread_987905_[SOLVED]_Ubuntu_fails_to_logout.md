---
title: "[SOLVED] Ubuntu fails to logout"
date: 2008-11-20
forum: Desktop Environments
---

### Post by zeneslev on 2008-11-20
I am running Ubuntu 8.10 with updated nvidia graphics drivers on my laptop. I have two sessions that I am maintaining, fluxbox and gnome. My problem is that now, for some reason, when I try to logout, the screen goes black for about a minute, goes to terminal where the last entry is something like "checking battery status", then goes black again, then the nvidia logo appears followed by yet another black screen and an error message titled "Ubuntu is running in low-graphics mode" "The following error was encountered. You may need to update your configuration to solve this. (EE) Failed to load module "type1" (module does not exist, 0)" I cannot advance past this point and get back to the logon screen.

I've looked around and I have tried 

```
sudo dpkg-reconfigure xorg
```
but the reconfiguring does not seem to help my issue.

Any ideas or information needed?
Thanks in advance.

---

### Post by zeneslev on 2008-11-20
bump

---

### Post by zeneslev on 2008-11-20
problem solved. It seems that the bleeding edge nvidia drivers failed me.

---

