---
title: "how to add script to alacarte menu"
date: 2006-09-28
forum: Desktop Environments
---

### Post by tibbar on 2006-09-28
hi

this problem is driving me crazy... i have written a little script:

#!/bin/bash
cd /media/usbdisk
java -jar NW-E003_MP3_File_Manager-0.10.jar

which is saved as "sony".

I did chmod a+x and it runs from a bash terminal perfectly and now lives in /usr/bin.

How can i get this to run from the alacarte menu?  I tried adding it as:

sony
/usr/bin/sony
sh /usr/bin/sony

but none will work...

i'm almost about to write a little c program to do:
 
int ret;
char *cmd[] = { "/usr/bin/sony", (char *)0 };
...
ret = execv ("/bin/sh", cmd);

but this seems ridiculous...can anyone tell me how to get this to work?

---

### Post by CatKiller on 2006-09-29
Do you mean that you'd like to add a launcher to your Applications panel? Alacarte is the name of the editor, not the name of the menu. If the program is in your path, you should just be able to have sony as the command, although you might try checking the "run in terminal" box.

---

### Post by tibbar on 2006-09-29
yes simply adding it to the menu.

/usr/bin is in my path naturally, i can type "sony" from any bash shell without a problem, but as soon as i put this command into the menu, with or without the terminal option, nothing happens.

same problem applies to trying to do:

sh /home/tibbar/eDonkey/runDonkey.sh

from the menu.

This works in SUSE 10.1/KDE but not in Ubuntu/GNOME...

---

### Post by ryu kun on 2006-10-01
3 days but no answers..

Same problem here. I am trying to run "Memoranda" from the panel by adding a shortcut but, same problem, the script doesn't run from there...

I tried to make a link first then add the link to the panel but no avail..

I hope someone can post a solution.

---

### Post by tibbar on 2006-10-02
anyone...it can't be that hard...

---

### Post by ryu kun on 2006-11-04
Can't we add scripts to the panel in Dapper... ](*,)

---

### Post by lil'tyke on 2006-11-05
chmod 755 <path to>/bin/mp3mngr.sh

#!/bin/bash
mount /mnt/sda1
cd /mnt/sda1
/opt/jdk1.5.0_06/bin/java -jar /opt/mp3mngr/NW-E003_MP3_File_Manager-0.10.jar
cd /mnt
umount /mnt/sda1

Right click panel.
Add to Panel | Custom Application Launcher
In the Create Launcher window
Command: <path to>/bin/mp3mngr.sh 

To debug, tick Run in Terminal

---

### Post by Cruxic on 2006-12-10
I just posted my experiences to this related thread:
[How to add a menu item when application is launched from a script]("http://ubuntuforums.org/showthread.php?p=1870047#post1870047")
Perhaps it will help.

---

