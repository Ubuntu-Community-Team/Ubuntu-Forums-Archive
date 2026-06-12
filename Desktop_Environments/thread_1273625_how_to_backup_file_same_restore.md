---
title: "how to backup file same restore ?"
date: 2009-09-23
forum: Desktop Environments
---

### Post by tonjaa on 2009-09-23
[COLOR=Sienna]some time i try to install many program some program i don't know how to use it .
and it make my system and environment change but i don't know what's program running
like i ever install about gtk program and it change my desktop that time i don't understand
more between gtk and gnome that i want to know on Linux Ubuntu have some program
for backup or system restore same on Windows or not?  or how to backup and restore
system when have problem i can return to good  point  please guide to me.[/COLOR]

---

### Post by Giblet5 on 2009-09-24
[Here's some information for backup]("http://ubuntuforums.org/showthread.php?t=35087") and restore.

You can also use zip/unzip, 7zip, etc, which have Windows counterparts.

I use the rsync and tar commands, myself.

A "safe" way to recover from "experiments" is to execute the following commands from the console (Ctrl-Alt-F1).

Login as yourself:
```
cd ..
sudo /etc/init.d/gdm stop
sudo mv $HOME $HOME.backup
sudo mkdir $HOME
sudo chown $LOGNAME:$LOGNAME $HOME
sudo chmod 755 $HOME
sudo /etc/init.d/gdm start
```

You'll be able to login with the Ubuntu defaults settings, and **all of your documents, pictures, etc, are in ../yourname.backup** where you can selectively copy them to your new home.

---

