---
title: "Sync program"
date: 2005-12-01
forum: Desktop Environments
---

### Post by tazzik on 2005-12-01
Hi,
I am looking for a program to be able to sync 3 folders when attached, if possible, when told to if I have to though! I need to sync : /home/tayo/School Work (and all subfolders) to 1. /media/ipod/School Work 2. (network pc) \\MOORE4\School Work.
What have you used / recommend for this type of job, in windoze synctoy does the job fine, but can't do it on device connect, i e when \\MOORE4 turns on (and enters network) or when the iPod is connected, you have to tell it to sync to all the folders. (damn annoying really)
cheers
tazzik,

---

### Post by 23meg on 2005-12-01
Check out rsync.```
man rsync
``` Once you've decided on your exact rsync command line, enter it in the ipod section in System / Preferences / Removable Drives and Media / Multimedia and it will be executed when your ipod is mounted.

---

### Post by tazzik on 2005-12-01
is there any other way to sync stuff, like a separate program (rsync too hard) lol
cheers

---

### Post by Brent Dax on 2005-12-01
I use Unison to synchronize my laptop and desktop home directories with a folder on my server.  It's available in the Universe repository; I believe the packages are unison (command line) and unison-gtk (GUI).

It won't work automatically--you have to tell it when to sync.  You could probably write a cron job to periodically sync things, though.  (Remember, this is Linux, with its Command Line Tools of Automation +5.)

---

### Post by 23meg on 2005-12-02
You can probably use unison when your ipod is plugged in as well, using the same method I mentioned above. And rsync shouldn't be too hard; just read the manpage and figure out the command you need to use, remember, you only have to do it once.

---

