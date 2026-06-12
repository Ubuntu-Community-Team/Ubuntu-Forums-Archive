---
title: "Permission problems with mounted drives in XFCE"
date: 2005-08-09
forum: Desktop Environments
---

### Post by musicman2059 on 2005-08-09
I've recently switched over to XFCE and, although it's so much nicer to run on a slow system, I've come across problems trying to use mounted removable drives (Floppies, CD-ROMs/Rs/RWs) both in the terminal and in xffm.

I used to be able to manage my removable media fine with my normal account when using GNOME and Nautilus.  However, trying to do anything that would place, remove, or otherwise alter the data on any of them brings back "permission denied."

I've double-checked everything permission-wise.  In the case of my floppy drive in particular, I tried chmodding /media/floppy0 (my mount point) to 777 and it didn't do much.  I also took note of /dev/fd0 and saw the owner group was floppy, like it should be, and has the mode 660.  I also double checked that my account is in the floppy group and can access floppy drives, and it is.  It seems my account has all the sufficent permissions to do whatever with data on a floppy disk and other removable media, so why am I getting "permission denied?"  (I can still use sudo to accomplish all I want to do but it feels a bit annoying to have to sudo everything.)


In addition, I'm searching for a way to burn data on to CD-R(W)s using XFCE.  I know Nautilus had burn:/// but I haven't found anything in/for XFCE yet that would allow me to burn anything onto a CD.  Any suggestions?

---

### Post by varunus on 2005-08-09
Try loading gnome-volume-manager in XFCE and see if that fixes your permissions problems.

You could try gnomebaker for CD burning; XFCE can't burn naturally.

---

### Post by musicman2059 on 2005-08-10
[QUOTE=varunus]Try loading gnome-volume-manager in XFCE and see if that fixes your permissions problems.

You could try gnomebaker for CD burning; XFCE can't burn naturally.[/QUOTE]
 Tried loading in gnome-volume-manager.  It didn't solve anything.

---

