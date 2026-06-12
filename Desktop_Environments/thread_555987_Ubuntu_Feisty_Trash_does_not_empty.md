---
title: "Ubuntu Feisty Trash does not empty"
date: 2007-09-20
forum: Desktop Environments
---

### Post by zonum on 2007-09-20
All,

As of yesterday evening, it seems I cannot Empty Trash.  This is for myself, non-root.  Here is the situation.  I see that the Trash icon on the lower-right of the desktop shows that the Trash can is not empty, so I right-click and select Empty Trash.  The icon continues to be the same way, showing the Trash can is full.  

If I open the Trash (lower right of Desktop), it shows me a "console" folder and sometimes a "sudo" folder.  In the opened Trash window, if I click  on Empty Trash, it gives me an error for each item that says, for example: ' "/var/run/console" cannot be deleted because you do  not have permissions to modify its parent folder'

The question is, and I don't really know when this behavior occurred, why is it that /var/run/* contents are showing up (automagically), in the Trash.  Also, my .Trash folder (and root's, for that matter), are empty!  In order to get the Trash icon to show that it is empty, I have to "sudo rm -rf /var/run/*" then, and only then, does the Trash icon shows to be empty.

Any thoughts or comments will be greatly appreciated.  This is on Feisty 7.04.

Thanks,

zonum

---

### Post by Happy_Man on 2007-09-20
Did you try restoring the /var/run contents first? Perhaps you accidentally dragged something in by mistake.

---

### Post by zonum on 2007-09-20
There is nothing in /var/run after I "rm -rf /var/run/*" - however, automagically, as I said, a console folder shows up...

---

