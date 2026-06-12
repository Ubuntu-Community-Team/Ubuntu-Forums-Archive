---
title: "/var/lock/subsys"
date: 2009-10-08
forum: Desktop Environments
---

### Post by R. M. Frank on 2009-10-08
Hi,

I'm running into something quite stunning. I have a desktop running Ubuntu 9.04 and have installed netvault's backup. Everything was fine, until I started doing updates and rebooted. After each update and reboot the directory /var/lock/subsys would be gone. I have no clue what does this, but it prevents netvault from starting.

Has anyone had somehing similar? Any hints greatly appreciated.


Robert

---

### Post by Lars Noodén on 2009-10-09
my guess is that it is something specific to netvault, because /var/lock/subsys isn't part of the [normal filesystem hierarchy](http://manpages.ubuntu.com/manpages/jaunty/en/man7/hier.7.html). /var/lock/ is though and there's probably a defect in netvault that's not making the file or directory when it starts up.  

Take a look at the startup script for netvault and walk through the steps manually.

For what reason have you chosen netvault over a normal solution like a script with rsync+ssh or a normal package like bacula, keep or amanda?

---

### Post by R. M. Frank on 2009-10-12
The /var/loc/subsys is a directory which, apparently, is used by many daemons on other linus distributions. I wonder where the ubuntu daemons put there locks. 

I chose netvalut because we have a hetergenous environment, with many different OS and this one does the job quite well. 

Netvalut does indeed not create the subsys directory, because it is standard on other linuxes (fedore, redhat, centos, etc) - but then, netvault is officially not supported on ubuntu ...

Thanks for the clarification about the non-standard subsys, this is what I wanted to know.

Robert

---

### Post by godber on 2010-11-30
/var/lock is a tmpfs mount, its not persistent through reboots.

---

