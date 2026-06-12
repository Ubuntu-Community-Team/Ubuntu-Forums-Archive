---
title: "[SOLVED] Bizarre Apache problem"
date: 2008-07-01
forum: Debian
---

### Post by p_quarles on 2008-07-01
Starting late last night, and very much out of the blue, Apache decided to just stop working on my Testing box. There is no indication that it fails to load, but there is no process, the sites it is supposed to serve do not show up, and netstat indicates that it is not listening. 

I've tried all manner of shutting down and starting up (different arguments in both /etc/init.d/apache2 and /usr/sbin/apache2ctl), but nothing initiates it. Again, there is no "failed to initiate" message, just this:
```
root@my-comp:~# /etc/init.d/apache2 restart 
Restarting web server: apache2apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```
The duplication of "apache2" in this message is the *only* strange feedback I'm getting. 

I have *never* had any problems with Apache before, much less a problem with any application silently refusing to load. I'm kind of at a loss here. Any suggestions?

EDIT: Okay, it occurred to me to look at the error log, which has a bunch of these lines:
```
[Tue Jul 01 03:19:35 2008] [error] (2)No such file or directory: could not create /var/run/apache2.pid
[Tue Jul 01 03:19:35 2008] [error] apache2: could not log pid to file /var/run/apache2.pid
```
Now for the really weird part:
```
ls /var/run/
```
shows a file called apache2.pid. Attempting to look at it, on the other hand, I get rejected:
```
/var/run$ cat apache2.pid 
cat: apache2.pid: No such file or directory
```
Deleting it does the same thing:
```
rm: cannot remove `apache2.pid': No such file or directory
```
So, the problem here appears to be not much Apache as it is this particular broken file/link/whatever-it-was-but-no-longer-is.

---

### Post by p_quarles on 2008-07-05
Well, this turned out to have nothing whatsoever to do with Apache. /var/run/apache2.pid, along with a couple of other .pid files, had broken inodes. Running an fsck on the root filesystem fixed the problem.

---

