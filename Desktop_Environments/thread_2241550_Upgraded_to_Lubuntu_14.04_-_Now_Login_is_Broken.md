---
title: "Upgraded to Lubuntu 14.04 - Now Login is Broken"
date: 2014-08-26
forum: Desktop Environments
---

### Post by redbikemaster on 2014-08-26
I recently upgraded from Lubuntu 12.10 to 13.10 using 
```

sudo apt-get dist-upgrade

```

After this, the login screen wouldn't come up. It would flash the background and the mouse, then the screen would go black and stay black. After searching for hours, I decided to try upgrading again to 14.04 to see if that would fix it. It didn't.

I used
```

sudo apt-get do-release-upgrade

```
To upgrade to 14.04. I get a login screen now, but if I try to login, the screen tears then freezes. The mouse is the only thing working. I can switch to another runtime, however.

Please help, as I need this laptop for school tomorrow morning for my web development class! My only other option is to use my Samsung Galaxy to program, which isn't fun at all.

---

### Post by grahammechanical on 2014-08-26
First of all the command dist-upgrade does not upgrade from one version of Ubuntu to the next version of Ubuntu. It does a smart upgrade of the existing version of Ubuntu.

Second, we cannot go from Ubuntu 12.10 to 13.10. We would have to go to Ubuntu 13.04 first.

Third, 12.10; 13.04 and now 13.10 have all reached end of life.

So, I really do not know what version of Ubuntu you now have but I doubt that it is 14.04.

My suggestion is to try Recovery Mode from the Grub boot menu. Then at the Recovery menu select Resume. That may get you to a working desktop using an open source video driver. If you get to a desktop then use Additional Drivers to activate an open source video driver or experiment with other proprietary video drivers. 

The Recovery menu will also give us Network which will establish a network (internet) connection and Root which will take us to a root shell prompt. There  we can run these commands to identify the version of Ubuntu.

```
lsb_release -a
uname -a
```

And these commands to update the system. Note any error messages. They might identify broken packages that are causing this problem.

```
apt-get update
apt-get upgrade
```

To get back to the recovery menu from the root shell prompt type exit.

Regards.

---

### Post by redbikemaster on 2014-08-26
I watched it upgrade from 12.10 to 13.10. If I type 
```

lsb_release -a

```

I get 14.04 LTS 'trusty' as a result. All the apt-get commands have been run with no resulting errors multiple times.

---

### Post by redbikemaster on 2014-08-26
I realize they were EOL, that's what started this epic in the first place.

---

### Post by ibjsb4 on 2014-08-26
> **redbikemaster said:**
> I recently upgraded from Lubuntu 12.10 to 13.10 using 
```

sudo apt-get dist-upgrade

```

"apt-get dist-upgrade" does not perform distribution upgrade. See

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by redbikemaster on 2014-08-27
Then I have a couple questions more. Why does it say '14.04'? How do I fix this?

---

### Post by ibjsb4 on 2014-08-27
> Why does it say '14.04'?
Thats a good question since you used another bogas command to get there.
> **redbikemaster said:**
> I used
```

sudo apt-get do-release-upgrade

```
To upgrade to 14.04.

---

### Post by Rob Sayer on 2014-08-27
I do a clean reinstall rather than upgrade now, and my advice to the OP to clean up this mess is to back up his/her data and do the same.  I've reinstalled for less.

---

