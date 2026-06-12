---
title: "Problems Add/Remove Programs Ethereal"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Rival9999999999 on 2006-07-13
Just switched to Linux. i have the new version of ubuntu with all the updates. I went into add and remove programs to add Ethereal. When i try to add it i receive the following error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

when i go into the terminal and try to run "dpkg --configure -a" i recieve the following error "dpkg: requested operation requires superuser privilege"

What do i have to do? i am logged in as the only and primary user account

---

### Post by Rival9999999999 on 2006-07-14
bump for fast help

---

### Post by gurgle on 2006-07-14
in terminal, run:

sudo dpkg --configure -a


this will give you temporary superuser rights.

---

### Post by Rival9999999999 on 2006-07-14
when i go into the terminal and try to run "dpkg --configure -a" i recieve the following error "dpkg: requested operation requires superuser privilege"

---

### Post by TheBlackNoodle on 2006-07-14
The primary account for Ubuntu is not "root" like in Windows. So don't forget the sudo, like gurgle said. You should be prompted for your password. Then you'll have superuser privileges for the following command.

---

### Post by Rival9999999999 on 2006-07-14
sweet!! I missed the sudo

---

