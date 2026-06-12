---
title: "what's wrong with my script"
date: 2009-06-14
forum: General Help
---

### Post by sn0m on 2009-06-14
Hi guys, I have written a simple rsync script to backup my laptop to my desktop.
I do not want the directory downloads in my home directory to backup, so used exclude option but no success.
I'd apppreciate if someone could tell me what is wrong in here;
script as follow:

#!/bin/sh
#script to backup in remote desktop
#i have set up connection already using a tutorial here
/usr/bin/rsync -Pvrue /usr/bin/ssh /media/sda4/ [email]sn0m@sn0m-desktop.local[/email]:/media/sdb1/sn0m-laptop-backup/ 
/bin/sleep 20s &&
/usr/bin/rsync -Pvrue --exclude 'downloads/' /usr/bin/ssh /home/koli/ [email]sn0m@sn0m-desktop.local[/email]:/media/sdb1/sn0m-laptop-backup/home-backup/ 
#/usr/bin/rsync -qaruzP -e /usr/bin/ssh /media/sda4/ sn0m-desktop.local:/media/sdb1/sn0m-laptop-backup/
######nowclose connection

---

