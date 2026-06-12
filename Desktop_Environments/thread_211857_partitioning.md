---
title: "partitioning"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Fittersman on 2006-07-09
when partitioning with the new ubuntu 6.06 what are all the partitions used for?

like what is "/" partition for and "swap".... 

do i need all of them for ubuntu to work?

---

### Post by aysiu on 2006-07-09
**/** is the top-level directory under which all other directories live. This partition is mandatory, just as **C:\** is mandatory in Windows.

**swap** is sort of like additional RAM but slower.

All other extra partitions (/home, /var, /boot, /usr) are optional.

---

### Post by Fittersman on 2006-07-09
thanks, what are the optional ones for?

---

### Post by aysiu on 2006-07-09
> **Fittersman said:**
> thanks, what are the optional ones for?
Well, let's say you want to reinstall Ubuntu, but you don't want to overwrite your settings and files.

How would you do it? Answer--you can't. Because the settings and files are in your /home/fittersman folder, which is just a folder living inside of your / partition. You can't tell the installer "Yes, install over everything, but leave this folder alone."

The installer doesn't know *folders*. It knows *partitions*.

If you have a separate /home *partition*, you can tell the installer, "Use this partition as my /home folder and don't erase it, but use the other partition as my / folder and reformat it."

---

