---
title: "GDM Error &quot;could not start the x server&quot; 9.04 troubleshoot"
date: 2009-05-22
forum: General Help
---

### Post by orpheus743 on 2009-05-22
I have been on Ubuntu for a few months now (still a newb) and am currently running 9.04 Jaunty on an old HP Pavilion ze5170 laptop. Today, I was using my laptop when out of the blue it shut down. Upon reboot, I got the following error message:
 
Could not start the X 
Server due to some internal error.
Please contact your sysem adminstrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart GDM when the 
problem is corrected
 
There was also a login line for Terminal below so I logged in there and took my laptop to an internet café and searched the forums. There are a few other threads on similar topics but nothing recent and nothing that solved my problem. A quick recap of the advice posted elsewhere:
 
Apparently this has something to do with my video card
I ran this suggested code:
"sudo dpkg-reconfigure -phigh xserver-xorg"
only to be told "cp: cannot creat regular file `/etc/x11/xorg.conf.20090522143714': Read-only file system"
 
Also, I am now repeatedly receiving this message: "* Stopping anac(h)ronistic cron anacron"
 
I'm at a loss since I haven't (knowingly) touched the fstab and the forum fixes haven't worked for me because I'm in read-only. I have a LiveCD for 8.10 and so could potentially reinstall OS but I'm concerned that I would lose some important files. Any help would be greatly appreciated. Please keep in mind that I am a newb and need things spelled out for me. My only computer access now is at a web cafe so I will be checking in regularly but won't be available immediately, hopefully this is enough information for someone with more knowledge than myself to see the problem and solution. On a side note, I wasn't totally sure where to post this, hope I didn't choose the wrong forum.

---

### Post by Lajik on 2009-06-04
I get this same error!  All of a sudden out of the blue when I tryed booting up to ubuntu that is what happens.  I'm on a dell studio 1550, just upgraded to 9.04 from 8.10 yesterday.  I guess my first question is what is the syslog and how to i check it?

---

### Post by listener on 2009-06-04
I'm not at all sure.  The filesystem should
not be 'read-only' though.   It can do this
if there is a problem with your hard drive
or the filesystem has become corrupt somehow.
If the root filesystem is r/o it may explain
why you are having problems.  

To see what is in the syslog, just do something
like:

```
tail -n 60 /var/log/syslog
```

which will show you the last 60 lines of your
system log.  Also you can try:

```
dmesg | tail
```

which is similar.  

I wish I could help more.  If either of you need
to re-install, you probably can mount the filesystem
to retrieve important data if you can preserve it
(not overwrite the partition).

---

