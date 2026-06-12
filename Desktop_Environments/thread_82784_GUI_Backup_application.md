---
title: "GUI Backup application?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Gordonbp531 on 2005-10-27
Anyone got any good recommendations for this?

---

### Post by pitr on 2005-10-27
[quote=gendibal]Anyone got any good recommendations for this?[/quote] 
sbackup [http://sourceforge.net/projects/sbackup]("http://sourceforge.net/projects/sbackup") might be what you are looking for. It is in the repositories so you should be able to find it in synaptic.

---

### Post by Gordonbp531 on 2005-10-27
I tried that last night - couldn't get it to work. I'll have another go tonight.

---

### Post by waffen on 2005-10-28
[QUOTE=gendibal]I tried that last night - couldn't get it to work. I'll have another go tonight.[/QUOTE]
Me too...I try in the console sbackup and nothing, what is the correct command to run the app ??

---

### Post by Remmelas on 2005-10-28
[QUOTE=waffen]Me too...I try in the console sbackup and nothing, what is the correct command to run the app ??[/QUOTE]
This is probably the one thing that bugs me about Ubuntu, is when software doesn't show up in the menu, how user friendly is that.  

the executables installed for this app are
/usr/sbin
/usr/sbin/sbackupd
/usr/sbin/simple-backup-config
/usr/sbin/simple-restore-gnome
/usr/sbin/srestore.py
/usr/sbin/upgrade_backups.py

although I haven't actually read the docs to figure out how to use it, so, not sure which you'd actually want to execute.  From the file installed in /usr/share/menu it looks like simple-backup-config and simple-restore-gnome are your friends

---

### Post by Darrin on 2005-10-28
I just installed Simple Backup.
I just installed it. I dont know about the command line, but via GUI Its in Menu>System>Administration. It works well. By default it backs up files to /var/backup.

---

### Post by Remmelas on 2005-10-29
Yeah, i'm a dink, didn't eve think to look at the Admin menu

---

### Post by waffen on 2005-10-29
[QUOTE=Darrin]I just installed Simple Backup.
I just installed it. I dont know about the command line, but via GUI Its in Menu>System>Administration. It works well. By default it backs up files to /var/backup.[/QUOTE]
Uhm...yes it is! but I need restart my laptop for the icon program apears... :-(

---

### Post by Trab on 2005-10-29
[QUOTE=waffen]Uhm...yes it is! but I need restart my laptop for the icon program apears... :-([/QUOTE]
not true.
open a shell and type
```
killall gnomepanel
```
it will restart the gnome panel and should have the new icon added...
cheers
-Trab

---

### Post by Darrin on 2005-10-29
[QUOTE=waffen]Uhm...yes it is! but I need restart my laptop for the icon program apears... :-([/QUOTE]
Hmmm. Mine was there right away after I installed it.

---

