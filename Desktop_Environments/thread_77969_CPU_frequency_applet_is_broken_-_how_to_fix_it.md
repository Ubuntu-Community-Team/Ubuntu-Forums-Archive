---
title: "CPU frequency applet is broken - how to fix it?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by tbraun on 2005-10-17
Hello!

I recently upgraded from Hoary to Breezy. At first, the CPU frequency applet worked fine. Then I tried the Automatix application to perform some aditional tweaking. It also fiddled with powernowd, and as a result, neither CPU scaling nor the CPU frequency applet worked anymore.

So I rolled back the changes to powernowd, which works again as before. However, the CPU frequency applet remains broken. Has anyone else seen this? How can I get it work again? I mean, it used to work before I ran Automatix.

Any help would be greatly appreciated.

Tom

---

### Post by DarkB on 2005-10-18
my powernowd has also stopped working ... How did you get it to work again ... how did u roll-back the changes?


thanx

---

### Post by ted209 on 2005-10-18
It also broke my powernowd!

I fixed it by restoring the /etc/init.d/powernowd_backup and /etc/acpi/power.sh_backup files.  These are made by Automatix, so just delete (or rename to be safe) the existing files, then remove the _backup from these files.

Ed

---

### Post by tbraun on 2005-10-18
Yes, that's how you roll back the changes to powernowd. But did your CPU frequency applet work again after that? I still would like to know how to get that to go again.

Tom

---

### Post by ted209 on 2005-10-18
yes, the CPU frequency monitor panel now shows that the CPU speed is changing with CPU load.

Ed

---

