---
title: "missing turn off power button"
date: 2006-09-09
forum: Desktop Environments
---

### Post by syd2o2 on 2006-09-09
I don't have a turn off computer button anymore. The others (restart, switch off, hibernate...) are still there.
I don't know if that is the reason, by I installed some new login and splash screns.
Anybody know how I can get it back? Can't turn the computer off, except on the power button on the case.

---

### Post by mandrakethepenguin on 2006-09-09
Try typing this in a terminal:
```
sudo dpkg-reconfigure acpi-support && sudo dpkg-reconfigure acpid
```

---

### Post by bbarrons on 2006-09-10
okay, I have been searching for a fix for this problem for a month. Could you tell me why this works? I dont know what acpi support has to do with the buttons missing and will this happen again after reboot???
I know of 2 different threads already that no one has really answered. This is the first solution that worked.....

---

