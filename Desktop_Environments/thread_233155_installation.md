---
title: "installation"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Digidiz on 2006-08-09
i somehow cannot install breezy dapper 6.06 when i put install acpi=off there is a prompt saying that there is an unknown mount and thats where it stops

---

### Post by ciscosurfer on 2006-08-09
You're trying to upgrade from Breezy Badger to Dapper Drake? Do it from within your current Breezy Badger system.  I believe you just need to reorganize your repos to point to Dapper deb's and deb-src's.  Then do a ```
sudo aptitude update && sudo aptitude dist-upgrade
```That should do it :D

---

### Post by Digidiz on 2006-08-09
no straight installation, from a dvd iso

---

### Post by Jagot on 2006-08-09
Have you checked the disk for errors?

---

### Post by Digidiz on 2006-08-10
no how do i do that on the installation disk?

---

### Post by Digidiz on 2006-08-10
> **Jagot said:**
> Have you checked the disk for errors?
 
 
just checked it but its still not working

---

### Post by tck on 2006-08-10
Ditto, having terrible problems.

First tried using DVD 6.06 Dapper, was PAINFULLY slow like when I got onto the desktop it took 10 mins to open a terminal and the espresso didn't even start properly. Tried Desktop and the same issues. 

Someone then recommended alternate version as they said this worked for them. So did a text install with Alternate and towards the end of installing packages it just hangs. I had turned off standy and all other power options beforehand in case this was the case.

Im installing this onto a Dell Inspiron 1300 256 ddr2 ram.

So I get the new Dapper 6.06.1 today, and same issue with the Desktpop, PAINFULLY slow and unusable. 

Now trying to get the alternate 6.06.1 dapper.

Anyone else getting these issues?

---

### Post by Digidiz on 2006-08-10
mine just keeps saying loading drivers and its just stuck there, when i tried this with the option "install acpi=off" it keeps saying that the mount is unknown

---

### Post by Digidiz on 2006-08-13
this is what i am getting

---

### Post by the-linux-guy on 2006-08-13
use "install root=/dev/hda3 ro noapic nolapic acpi=off" (use the hda-number that applies to you, of course) or try with a text-based install only ?
Good luck !

---

### Post by Digidiz on 2006-08-13
the problem is i want to install it on my sata drive 1 partition 3 which i hopefully will install on that one i want to install on
 
is it sda something?

---

### Post by ciscosurfer on 2006-08-13
Yes it's sda if your drive is SATA. So try this```
install root=/dev/sda3 ro noapic nolapic acpi=off
```

---

### Post by Digidiz on 2006-08-13
mmmm not working :evil:

---

### Post by ciscosurfer on 2006-08-14
Please post your fstab```
cat /etc/fstab
```

---

### Post by Digidiz on 2006-08-18
> **ciscosurfer said:**
> Please post your fstab```
cat /etc/fstab
```
 
 
sorry how do i do that? under boot options?? (F6)??

---

