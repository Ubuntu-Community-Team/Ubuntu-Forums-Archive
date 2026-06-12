---
title: "Additional file in thunar.."
date: 2015-04-09
forum: Desktop Environments
---

### Post by Jahidul_Hamid on 2015-04-09
Whenever I edit a file, another file named filename~ is created and it remains on the folder permanently. I don't see any option in thunar to disable it. So, what is causing this unexpected behavior, can anybody help?

It's Xubuntu 14.04.1 LTS
File  manager thunar 1.6.6
XFCE 4.12
N.B: It doesn't depend on the thunar or xfce version. older version did this too, It's becoming annoying...

---

### Post by grahammechanical on 2015-04-09
That file is a backup copy. It also is a hidden file so that a file manager such as Thunar and Nautilus will only see them if Reveal Hidden files is enabled.

These files can be deleted if we run the file manager with administrator or root privileges. It should also be possible to change the settings in Thunar so that it does not automatically save a backup of the file being edited. I do not use Thunar so I cannot tell you how to do that.

Regards.

---

### Post by Impavidus on 2015-04-09
Several applications, gedit for example, can automatically create backups of the files you're editing. This can be switched off in the application your use for editing the file. gedit appends ~ to the filename to create the backup. I don't know about the default text editor in Xubuntu (mousepad), as I always use vim.

Those backups can be deleted in the file manager like any other file. Only if the application that created the backup ran as root, you need root privileges to delete it.

---

### Post by CantankRus on 2015-04-09
Look at the settings of your text editor not the file manager.

---

### Post by Jahidul_Hamid on 2015-04-09
I got it, It's gedit. thnx guys...

---

