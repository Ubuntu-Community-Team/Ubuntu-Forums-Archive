---
title: "Removing Akonadi, Nepomuk and PIM generally"
date: 2011-05-21
forum: Desktop Environments
---

### Post by akoskm on 2011-05-21
Hi!
I'm not using any of the KDE PIM components (I already removed Kontact, KOrganizer, KMail, Kopete) but some akonadi tasks (~15-20) are always running in the background.
How can I get rid of akonadi and nepomuk completely without removing the actual KDE desktop?

---

### Post by demilord on 2011-05-23
you might try to disable the services.. also look in /usr/share/kde/autostart and other autostart directories..

---

### Post by Zorael on 2011-05-30
I managed to disable both Akonadi and Nepomuk on my laptop but I have been unable to reproduce it on my desktop. Moreover I can't find the blog post that described how to do it.

Going by memory...
[list=1][*]Add these lines to **~/.kde/share/config/nepomukserverrc** (and their sections if they don't exist);
```
[Basic Settings]
[COLOR="Green"]**Start Nepomuk=_false_**[/COLOR]

[Service-nepomukmigration1]
[COLOR="Green"]**autostart=_false_**[/COLOR]

[Service-nepomukstrigiservice]
**[COLOR="Green"]autostart=_false_[/COLOR]**
```
[*]Then, in **~/.config/akonadi/akonadiserverrc**, add the line in bold to this section (other lines may differ);
```
[QMYSQL]
Name=akonadi
Host=
User=
Password=
Options="UNIX_SOCKET=/home/zorael/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
**[COLOR="Green"]StartServer=_false_[/COLOR]**
```
[*]Lastly remove the file **/usr/share/autostart/nepomukcontroller.desktop**, if it exists.[/list]
Log out, wait a bit for the processes to end, and then back in. See if it still starts all those nepomuk and akonadi processes. Do mention here if it works, or if it doesn't and you find an additional step that completes it all.

As a small mention, you can still kill all the processes with two commands;
```
$ akonadictl stop
$ killall nepomukserver
```
But that's messy.

---

### Post by akoskm on 2011-06-01
Worked perfectly.
Many thanks! :)

---

### Post by pecosdave on 2012-05-16
Best help and walk-through on this subject ever!

---

