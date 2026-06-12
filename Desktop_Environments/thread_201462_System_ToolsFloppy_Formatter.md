---
title: "System Tools/Floppy Formatter"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Sweezel on 2006-06-21
If I take a rare earth magnet and erase a floppy disk, Ubuntu System/Floppy Formatter cannot determine the disk geometry and fails miserably.

If I do this in WinXP, it formats the floppy as expected.

Why can't the Floppy Formatter utility in Ubuntu do the same formatting/recovery as WinXP???

With such an old piece of hardware, you would think Linux would have this nailed. Is this some sort of security feature???

---

### Post by llamakc on 2006-06-21
Unless  you have tried this on other GNU/Linux distros you should edit the last sentence to : *Ubuntu would have this nailed.*

Are you trying to format from the commandline or from some GUI app?

---

### Post by Sweezel on 2006-06-21
It appears to be a problem with Mac formatted disks as well.

Does anyone have any insight as to why the command line utilities can't handle these issues?


Thanks,

Staci

---

### Post by Sweezel on 2006-06-21
Sorry, I didn't see your reply before I sent mine.

I am using the floppy formatting GUI available in Ubuntu Gnome.

---

### Post by Sweezel on 2006-06-21
I bought Mac formatted disks from eBay and Windows appears to be the best utility for changing them to DOS format.

God that sucks...

---

### Post by llamakc on 2006-06-21
Have you tried fdformat from the commandline?

---

### Post by Sweezel on 2006-06-22
I have found that you can format a completely blank disk on the command line with:

**setfdprm -p /dev/fd0 1440/1440** and then **fdformat /dev/fd0**

I am surprised that the floppy density selection in Gfloppy doesn't set these parameters for you. 

If I run the **setfdprm -p /dev/fd0 1440/1440** command just before formatting in Gfloppy, everything works fine.

In other words, Linux pukes on a floppy that does not already have a recognizable file system unless you run setfdprm just before the format.

---

