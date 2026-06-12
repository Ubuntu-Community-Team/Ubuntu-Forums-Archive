---
title: "Automatic Backup to USB Thumbdrive?"
date: 2009-03-20
forum: General Help
---

### Post by Mewshi on 2009-03-20
Hello again >.>

Anyway, I just bought a SanDisk Cruzer Micro.  After removing the utter crap known as U3, I have a nice little drive I can use anywhere.  I have portable apps on here :D

Anyway, what I would like to do is have it automatically back up certain files as soon as the drive is mounted - schoolwork, mostly...

Any ideas are *very* welcome ^_^

---

### Post by detroit/zero on 2009-03-20
I also wouldn't mind seeing an answer to this question.

---

### Post by LoneWolfJack on 2009-03-20
is there anything that would advise against the use of rsync+crontab?

---

### Post by 1ronlung on 2009-03-20
If you want to use imaging software that's specific to particular files/folders, have a look at :
[http://www.thefreecountry.com/utilities/backupandimage.shtml](http://www.thefreecountry.com/utilities/backupandimage.shtml)

It's 50% win and 50% Linux software listed ...

---

### Post by fragos on 2009-03-20
You may find unison easier to use than rsync for this application. Unison can run GUI or from the CLI. I'd think twice about automatically running the backup and would favor the GUI unison which allows to to have multiple backs you can select from. The GUI unison gives you manual control to select which file image to use when both source and destination have changed since the last time unison was run.

---

### Post by ushills on 2009-03-20
+1 for Unison.

It has a nice GUI and i use it to sync to usb everytime i insert my usb. this way i can edit my /home docs anywhere and sync between pc and usb.  it's very good.

---

### Post by Mewshi on 2009-03-20
But I want it to sync *automatically* on insert... and every half hour while it's in would be cool, too :)

---

### Post by ushills on 2009-03-21
> **Mewshi said:**
> But I want it to sync *automatically* on insert... and every half hour while it's in would be cool, too :)
You can use unison command line and set up a anacron and cron job to sync on start and every 30 mins.

---

### Post by Mewshi on 2009-03-21
No, because the drive isn't always in at start...

---

