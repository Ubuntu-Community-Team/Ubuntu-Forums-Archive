---
title: "synaptic damaged?"
date: 2009-01-15
forum: General Help
---

### Post by eggy1962 on 2009-01-15
Hi, when i was attempting to install limewire the pc seemed to hang, after  a restart i again attempted to install limewire when met with this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 any help to rectify this would be appreciated, please note i am a novice linux user

---

### Post by Titan8990 on 2009-01-15
As a novice Linux user I am going to teach you something very important. Unlike Windows where error messages are a bunch of useless crap that leads you in a wild goose chase, Linux error messages are almost always useful and should be examined closely.

So lets examine your error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```


This error message tells us to manually run 'dpkg --configure -a' and that is exactly what we are going to do. It **will** fix the problem.


Go to Application -> Accessories -> Terminal

Type the follow and hit enter:

sudo dpkg --configure -a


Good luck and welcome to Linux!

---

### Post by eggy1962 on 2009-01-15
mark@mark-desktop:~$ sudo dpkg --configure -a
[sudo] password for mark: 
Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
mark@mark-desktop:~$ 

Has this cured it? or do i need do anything else?

---

### Post by Titan8990 on 2009-01-15
That is it :)

---

### Post by eggy1962 on 2009-01-15
yes it is , all i had to do was  upgrade/repair the java  then limewire installed ok.
Thank you for your assistance.
if any moderators around.... this one could be marked as solved

---

### Post by Twitch6000 on 2009-01-15
> **eggy1962 said:**
> yes it is , all i had to do was  upgrade/repair the java  then limewire installed ok.
Thank you for your assistance.
if any moderators around.... this one could be marked as solved

the solved button on the forum is currently out of order due to technical issues.

---

