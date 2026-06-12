---
title: "How can you uninstall a Windows application completely (in Xubuntu)"
date: 2007-10-18
forum: Desktop Environments
---

### Post by jis on 2007-10-18
I installed Syder2PRO 2.3.5 (available [here]("http://support.colorvision.ch/index.php?_m=downloads&_a=viewdownload&downloaditemid=41&nav=0")) using wine. If I remember right, I uninstalled it later by Applications > Wine > Wine Software Uninstaller. However, in the menu there are some items of  the Syder2PRO in Other menu. How can you completely remove the app?

I am using Xubuntu Feisty PC (Intel x86). 

BTW. Monitor profiling solution that works also in linux would be nice.

---

### Post by ajgreeny on 2007-10-18
You can certainly just delete the folder in ~/.wine/drive_c/Program Files/foldername that the program made on installation.  This will contain most of the program files for that program but others may still remain (a few dll etc in the ~/.wine/drive_c/windows folder), but they will not take a great deal of space, I suspect, so you can probably leave them and not worry.  Anything left in the xubuntu menu can I assume be deleted using whatever menu editor xubuntu has.

---

### Post by jis on 2007-10-18
Thanks, ajgreeny, but the problem is that Xubuntu's menu editor does not let me alter items that it has automatically added (nor does it show them).

---

### Post by ajgreeny on 2007-10-18
OK, sorry but I don't know xubuntu so didn't realise that, and I'm afraid I can't help any further on the problem.

---

