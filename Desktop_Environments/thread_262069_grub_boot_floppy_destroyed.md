---
title: "grub boot floppy destroyed"
date: 2006-09-21
forum: Desktop Environments
---

### Post by johnleonard on 2006-09-21
Hi  - I have a dual boot machine which by default boots to XP, with Dapper accessible using Grub on a floppy. This worked well until idiocy struck: while trying to duplicate my Grub boot floppy I accidently reformatted it (forgetting to replace my boot floppy with a new one). Doh!

So, I now have no working copy of Grub, and am unable to boot into Ubuntu. 

How do I create a new boot floppy that will allow me back in? Any help much appreciated!

John

---

### Post by lagagnon on 2006-09-21
Put your Ubuntu Live CD back in the machine and boot it, using ubuntu recovery. Then run grub-install. Might wanna read up on grub-install before you do it. (man grub-install).

---

