---
title: "help please...:)   cannot login to server"
date: 2009-04-16
forum: General Help
---

### Post by caperpc on 2009-04-16
woke up to me not being able to ssh in ....with this error
“Cannot execute /bin/bash: Too many files open.”

Plugged in a monitor and tried to login with the same result
Cannot find any info on this...only tripped over the following url which is exactly what I see.
 
[http://www.stuff.za.net/?p=207](http://www.stuff.za.net/?p=207)


thanks a million
p

---

### Post by bgerlich on 2009-04-16
Your system has to many files open. This can be caused by a faulty script, error in a program, or overuse of system resources. Could be also that you didn't cause this but someone else took over your server and caused those errors. Try rebooting and if you need a higher number of open files you can try to play with the file-max parameter in /proc/sys/fs/file-max .

---

