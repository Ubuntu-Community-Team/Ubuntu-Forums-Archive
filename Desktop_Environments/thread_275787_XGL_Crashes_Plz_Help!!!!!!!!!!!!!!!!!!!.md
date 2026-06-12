---
title: "XGL Crashes Plz Help!!!!!!!!!!!!!!!!!!!"
date: 2006-10-11
forum: Desktop Environments
---

### Post by marco999 on 2006-10-11
I am running Dapper with XGL + Beryl, on an Compaq Presario 2170US. Beryl/XGL crashes when I recieved any notifications via the system tray for updates. It not only totally freazes but messes up the display and puts black and grey boxes through it. After this I can not even log out or anything thus I am forced to hard boot.

I will add the log file to the post. Tho I need to know where the log is located. Does anyone know this?

Also if there is a way to fix this Plz reply to this post on how I do so!!!!!

Marco999

---

### Post by catanzag on 2006-10-12
All the logs are in /var/log; you can check Xorg.*.log for X errors or messages for general system errors

catanzag

---

### Post by marco999 on 2006-10-12
My log file is added as a attachment to this post.

---

### Post by catanzag on 2006-10-12
There is another thread [http://www.ubuntuforums.org/showthread.php?t=275216](http://www.ubuntuforums.org/showthread.php?t=275216) dealing with a similar problems (XGL doesn't work and the only error in Xorg.0.log is /dev/wacom not present); I posted there some tips, though I'm not sure that they could work. However you can try them.
 	
BTW, *Xorg.0.log.old* is a backup, the last one is *Xorg.0.log*; you can check if there are different errors (the lines marked with **(EE)**)

Have a good job

regards

catanzag

---

### Post by catanzag on 2006-10-13
There is another suggestion if you follow [this]("http://www.ubuntuforums.org/report.php?p=1606485") post to reconfigure your xorg.conf if everithing else doesn't still work

---

