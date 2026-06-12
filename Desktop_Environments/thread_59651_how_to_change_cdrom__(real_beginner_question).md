---
title: "how to change cdrom ? (real beginner question)"
date: 2005-08-24
forum: Desktop Environments
---

### Post by obladi on 2005-08-24
I boot my ubuntu system up.
I log into GNOME.
I insert the first cd of MATLAB into the cd-rom.
I start the installer program.
The installer program needs to change cd to the second one.

I can't change it. I can't even open the cd-rom.
How can I change cd-rom?
I tried to umount /media/cdrom, but failed with the message "cdrom is busy"

---

### Post by arnieboy on 2005-08-24
[QUOTE=obladi]I boot my ubuntu system up.
I log into GNOME.
I insert the first cd of MATLAB into the cd-rom.
I start the installer program.
The installer program needs to change cd to the second one.

I can't change it. I can't even open the cd-rom.
How can I change cd-rom?
I tried to umount /media/cdrom, but failed with the message "cdrom is busy"[/QUOTE]
try this:
```
umount -f /media/cdrom
```

---

### Post by SGC on 2005-08-24
Also try this simple command:
```
eject
```

---

### Post by arnieboy on 2005-08-24
eject cannot **force unmount** a cd and eject it. so it wont work in this case.

---

### Post by LucasLinard on 2005-08-25
If you have the Cdrom icon showing on your Desktop, just click on it with you right button and choose eject.

---

### Post by arnieboy on 2005-08-25
[QUOTE=LucasLinard]If you have the Cdrom icon showing on your Desktop, just click on it with you right button and choose eject.[/QUOTE]
when the cdrom is busy, even that wont work. what u suggested is actually just a script using the "eject" command. it wont work as long as the cdrom is busy and cant be unmounted by default.

---

### Post by Yeeha on 2005-09-09
i have same problem with installing. I can unmount like that and get cd out and new cd in but it wont read new cd anymore even if i use mount command. Its real nasty problem, isnt there somekind of permanent fix for it?

---

