---
title: "Won't let me install things."
date: 2008-07-13
forum: Desktop Environments
---

### Post by Switched on 2008-07-13
Hi everyone,
  Every time I try to install things it comes up "Only one software management tool is allowed to run at the same time." I don't understand why it is saying this when I don't have anything else running. Could someone help me out?

---

### Post by tech0007 on 2008-07-13
Check if cron is running apt-get.

'ps aux | grep apt'

If it does, do

'sudo killall apt-get'

---

### Post by forger on 2008-07-13
it might be the update-manager doing a background check

---

### Post by Switched on 2008-07-13
> **tech0007 said:**
> Check if cron is running apt-get.

'ps aux | grep apt'

If it does, do

'sudo killall apt-get'

I tried that it didn't do anything.

I also checked to see if the update manager was running... I didn't see it on the list.

---

### Post by tech0007 on 2008-07-13
Try installing programs using the terminal

'sudo apt-get update'
'sudo apt-get [nameofprogram]'

it will spillout more specific details about the error.

---

### Post by Switched on 2008-07-13
Ok when I did 'sudo apt-get update' it went through a big list at the end it said 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
So I did 'dpkg --configure -a' which gave me this.
"dpkg: requested operation requires superuser privilege" 
Which really confused me since I am the only user on this computer.

---

### Post by perlluver on 2008-07-13
> **Switched said:**
> Ok when I did 'sudo apt-get update' it went through a big list at the end it said 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
So I did 'dpkg --configure -a' which gave me this.
"dpkg: requested operation requires superuser privilege" 
Which really confused me since I am the only user on this computer.

Run ```
sudo dpkg --configure -a
``` that should take care of it.

---

### Post by tech0007 on 2008-07-13
try 'sudo dpkg --configure -a'

---

### Post by jerome1232 on 2008-07-13
> **Switched said:**
> Ok when I did 'sudo apt-get update' it went through a big list at the end it said 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
So I did 'dpkg --configure -a' which gave me this.
"dpkg: requested operation requires superuser privilege" 
Which really confused me since I am the only user on this computer.
 You need to run as root to give yourself escalated privileges. 'sudo' temporarily escalates you to root.
```
sudo dpkg --configure -a
```

---

### Post by Switched on 2008-07-13
Ok I did sudo dpkg --configure -a and I can install things! Thank you all for the help. :)

---

