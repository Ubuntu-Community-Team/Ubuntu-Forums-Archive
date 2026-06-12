---
title: "Samba: Could I restrict files types?"
date: 2008-06-04
forum: Education &amp; Science
---

### Post by robla64 on 2008-06-04
Hi,
At the school where I teach we have an open windows server share that the students and staff use to place documents on so they can be accessed from anywhere (we do not use individual logins)

Is there a way I could set up a Samba share that would not allow certain file types to be saved...like exe or zip for example.
Or is there an easy way to write a script that would find and delete certain file types every so often.

Any suggestions would be appreciated.
Rob

---

### Post by Prospero2006 on 2008-06-04
Hello there,

I teach in a Ubuntu middle school computer lab.([http://www.neisd.net/imak/computerlabpage](http://www.neisd.net/imak/computerlabpage)) 

I use samba, and several of the Windows labs in my hallway are also hooked up to samba servers. I've tweaked it out so that I can log all transactions and delete files that shouldn't be there. (You can't restrict file types.)

-By setting this parameter:
   log level = 3 vfs:1
I generate log files. I have some other configurations that specify how much disk space they can take up. If an inappropriate file shows up or someone's work gets deleted, I can grep through the logs for the filename and determine the time it happened and what ip_address deleted the file. (With a good seating chart and static ip addresses across the lab, I only had to bust one or two trouble makers before the word got out.)

  Here is my script to erase all unwanted files on the server:
         ```

find  /StorageDrive3/students -name '*.aup' -exec rm -f {} \;
find  /StorageDrive3/students -name '*.exe' -exec rm -f {} \;
find  /StorageDrive3/students -name '*.EXE' -exec rm -f {} \;
find  /StorageDrive3/students -name '*.MP3' -exec rm -f {} \;
find  /StorageDrive3/students -name '*.wav' -exec rm -f {} \;
find  /StorageDrive3/students -name '*.wma' -exec rm -f {} \;
find  /StorageDrive3/students -name '*.WMA' -exec rm -f {} \;

```
 As you can see /StorageDrive3/students is the general share.


-It's also a good idea to have a script like this running every 15 minutes to secure student data:
 ```

rsync -a -r /StorageDrive3/students /StoragDrive4/BackupFiles/

```
In this case StorageDrive4 is the backup drive.

Let me know if you have questions. I've been using Samba in my computer labs for 2 years now.

---

