---
title: "partimaged"
date: 2008-12-27
forum: General Help
---

### Post by compgeek83 on 2008-12-27
Trying to do a test run of a remote backup with partimaged,  I installed it from the repositories on my server and I am using SystemRescueCD on the client

I run "sudo partimaged -L" to start partimaged without requiring a login and I receive the status window as I should

on the client, i run partimage and select the normal options as well as selecting "connect to server" and giving it my server's ip address.  after selecting next I receive "Connection refused by server: incompatible networking options.  Try disabling login option for the server"

any ideas?

I'm wondering if it has something to do with SSL as the partimaged in the repos is compiled with SSL enabled by default.

---

### Post by 2hot6ft2 on 2008-12-27
Since the post is an hour old and I don't know the answer perhaps this might be of interest as another option. From another thread.
> Clonezilla, fastest ever cloning i have ever done is using CLONEZILLA(indeed it is top notch app).

i have cloned several HDD and networked machines with it, locally and on network with no problem what so ever. Great app for one off complete system state clone/backup

Last week I cloned my laptop's HDD 120GB locally within 35 mins.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by compgeek83 on 2008-12-27
someone else suggessted that but I dont really think it will work for my ongoing situation.

[http://http://ubuntuforums.org/showthread.php?t=1022250]("http://ubuntuforums.org/showthread.php?t=1022250")

---

### Post by compgeek83 on 2008-12-29
bump

anyhelp is appreciated, i've uninstalled and reinstalled partimage from synaptic, rebooted between, etc but thats not helping.

---

### Post by mintar on 2009-01-19
This also took me an hour to figure out.

**The solution:**
From the SystemRescueCd client, use "partimage-ssl" instead of "partimage". :)
(Thanks to [_this thread_]("http://www.sysresccd.org/forums/viewtopic.php?t=1380"))


Also you are right about the "-L" option. In /etc/init.d/partimaged (on the Ubuntu Server), replace
```
OPTS="-D"
```
by
```
OPTS="-D -L"
```.

Alternatively, in the file /etc/default/partimaged, add the line
```
OPTS="$OPTS -L"
```.

In either case, do a ```
sudo /etc/init.d/partimaged restart
``` afterwards.

---

