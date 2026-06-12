---
title: "unintsall :("
date: 2006-04-20
forum: Desktop Environments
---

### Post by kontaktzero on 2006-04-20
hello everyone. i am new to ubuntu and was never able to get into it because my windows partition was having problems that were diagnosed as coming from the ubuntu side. so anyway i now have to uninstall linux. i do not know how to do this so if anyone could point me in the right direction that would be great! 
thanks

stats:
Dell Dimension 3000, NTFS

---

### Post by BoboChimp on 2006-04-20
you don't really have to "uninstall" linux.  all you have to do is reformat that partition using another filesystem such as ntfs or fat32.

---

### Post by Mr Egg on 2006-04-20
I had to do this when I installed Ubuntu for the first time, so I had to uninstall it, then I decided to re-install it.

Okay, to uninstall pop in your Windows XP CD and restart the computer.
When asked if you want to go into recovery console to hit 'R' then do so.
When in the recovery console, log-in to your administrator account.
Once logged in type 'fixmbr' (without the '') and hit enter.
It will ask you if you're sure, say yes.
When it's done tell it to reboot the computer.
Boot back into the XP cd and don't go to the recovery console this time.
When in the partitioner, delete the Ubuntu partition.

And that's pretty much all there is too it :)

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=Mr Egg]
When in the partitioner, delete the Ubuntu partition.
[/QUOTE]
In windows, it's in control panel under administrative tasks (or similar) as disk management.

---

### Post by Mr Egg on 2006-04-20
[QUOTE=towsonu2003]In windows, it's in control panel under administrative tasks (or similar) as disk management.[/QUOTE]

When you are logged in Windows as an administrator, right-click on My Computer and click Manage.

---

