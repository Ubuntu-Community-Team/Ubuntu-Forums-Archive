---
title: "Desktop Doesnt load"
date: 2008-04-07
forum: Desktop Environments
---

### Post by ahmedwaseem2000 on 2008-04-07
Hi,

Few days back i tried updating to the version 8.04. I started installation during night time and in the morning when i woke up. the computer had restarted due to power failure. Now, when i try to login i get the blank desktop(even without the task bar). now when i try to get into recovery mode and try the command "sudo apt-get -f install" i get the error E: dpkg was interrupted you must manually run 'dpkg --configure -a'  to correct the problem. Again i try the command  dpkg --configure -a but it gets aborted with the error message "dpkg: ../../src/packages.c:252: process_queue: Assertion `|queuelen' failed. Aborted"

Please help me fix this.

Thanks,
Waseem

---

### Post by Crafty Kisses on 2008-04-07
You may want to try:
```
sudo dpkg --configure -a
```
You may also want to try and reconfigure your X server and to do this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ahmedwaseem2000 on 2008-04-07
Nope that didnt help me

---

