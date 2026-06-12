---
title: "Screen locks every time I close my laptop's lid"
date: 2005-08-05
forum: Desktop Environments
---

### Post by moxfyre on 2005-08-05
I just switched from Debian Unstable to Ubuntu Hoary and I absolutely love it, great desktop setup and GUI admin tools, etc!

The only problem I am having is this: every time I close my laptop's lid, the screen becomes locked and I have to re-enter my password when I open it.  This is annoying, and I can't figure out how to disable it... it's not mentioned anywhere in the Ubuntu docs, nor in any of the GUI desktop configuration dialogs.

Is there some ACPI setting or something like that which I need to change??

Thanks for any advice!

---

### Post by r0ll3r on 2005-11-17
Hi there,
this thread has a solution: [http://www.ubuntuforums.org/showthread.php?t=52363&highlight=disable+lid]("http://www.ubuntuforums.org/showthread.php?t=52363&highlight=disable+lid")

Just roughly: edit this file:
/etc/acpi/events/lidbtn

Comment out the action line by placing a # at the start of the line. This way, no action will happen, when you close your lid.

---

