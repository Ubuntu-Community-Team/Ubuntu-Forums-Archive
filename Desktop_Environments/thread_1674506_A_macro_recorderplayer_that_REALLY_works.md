---
title: "A macro recorder/player that REALLY works?"
date: 2011-01-24
forum: Desktop Environments
---

### Post by dewdrop_world on 2011-01-24
I just tried gnee based on a recommendation from this thread [http://ubuntuforums.org/showthread.php?t=227565&page=2](http://ubuntuforums.org/showthread.php?t=227565&page=2) and... it's a ghastly joke. Crashes immediately on clicking "record."

Which leaves the original question from that thread unanswered -- is there a macro recorder/player for gnome that Just Works?

James

---

### Post by Felixcm on 2011-01-25
I'm looking for a macro recorder too but haven't find anyone that works fine yet :s

anyone can help us

---

### Post by dewdrop_world on 2011-01-26
I found out from the xnee devs that there were some changes in X along the way that broke xnee about the time of the last "stable" release. Those have been fixed in later versions of the sources, but they aren't packaged yet.


I've downloaded the sources but can't build it because I'm stuck in dependency hell.


```
dlm@dlm-laptop:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is to be installed
                 Depends: libglib2.0-dev (>= 2.21.3) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Broken packages
```


*libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is to be installed*


Does anybody know how to fix that?

---

### Post by PGScooter on 2011-03-18
did you figure it out?

---

### Post by tycarp on 2011-07-24
I use AutoKey (autokey.googlecode.com).  Does most of what AutoHotkey for Windows does, and seems to be well supported, and works on 11.04.

I also tried gnee (very briefly), and got the same result you did.

---

