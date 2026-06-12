---
title: "make Wubi Ubuntu the default boot menu choice?"
date: 2009-04-07
forum: General Help
---

### Post by brucewagner on 2009-04-07
Any way you (developers) can make Wubi automatically set Ubuntu as the default (top listed) menu choice on the Vista boot menu....?

This way Ubuntu would boot by default... if the user presses no keys...  which would be MUCH preferable for the total novice users.

---

### Post by Eredeath on 2009-04-07
In windows, download [EasyBCD]("http://neosmart.net/dl.php?id=1") and use that program to edit the Bootloader menu. This is the easiest way that I know of, and have used it many times.

---

### Post by Shpongle on 2009-04-07
i havnt used windows in a while but in xp you can edit the boot options in the control panel -> system properties -> startup & recovery probly the same for vista ??

---

### Post by Eredeath on 2009-04-07
> **DillByrne said:**
> i havnt used windows in a while but in xp you can edit the boot options in the control panel -> system properties -> startup & recovery probly the same for vista ??

Vista is totally different, you can't edit the bootloader like that.

---

### Post by matmat07 on 2009-04-07
Just make sure to leave the 5 sec delay on. Else, like I experimented, you won't be able to boot on vista anymore unless you reconfigure bcd with  comand like on the vista recovery cd

---

### Post by ytsejam1138 on 2009-04-07
In Vista:

Control Panel > System

On the left side of the screen click Advanced System Settings

Click on the Advanced Tab.  Under Startup and Recovery click the Settings Button.

You should now see a menu that will let you select your default operating system.

---

### Post by Shpongle on 2009-04-07
i guess that solves that , thanks ytsejam for satisfying my curiosity

---

