---
title: "Cannot fix Error org.freedesktop.DBus.Error.Spawn.ChildExited"
date: 2011-09-08
forum: Desktop Environments
---

### Post by haddog on 2011-09-08
Is anyone getting the message:

"Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127" 

after every apt-get? If so what is it and how do I fix? apt-get is updating and upgrading but I have not yet been able to resolve the above error.

I am running Ubuntu oneiric (developmental branch) release 11.10, 3.0.0-10-generic #16-Ubuntu SMP kernel.

---

### Post by arbitrabbit on 2011-09-08
Same issue here. Is there a solution?

---

### Post by kimr1508 on 2011-09-08
Same here.

Just upgraded to Kubuntu 11.10 beta1 from Kubuntu 11.04

---

### Post by PaulW2U on 2011-09-08
Do you have kpackagekit installed? It's now been made obsolete and removed from the Oneiric repository. 

I removed kpackagekit and the error hasn't been seen since. ;)

[This thread belongs here - [http://ubuntuforums.org/forumdisplay.php?f=403]](http://ubuntuforums.org/forumdisplay.php?f=403])

---

### Post by claydoh on 2011-09-08
> **PaulW2U said:**
> Do you have kpackagekit installed? It's now been made obsolete and removed from the Oneiric repository. 

I removed kpackagekit and the error hasn't been seen since. ;)

[This thread belongs here - [http://ubuntuforums.org/forumdisplay.php?f=403]](http://ubuntuforums.org/forumdisplay.php?f=403])

It didn't fix it for me.

---

### Post by haddog on 2011-09-08
Fyi. Bug confirmed.

__________________________________________________________________

** Changed in: apt (Ubuntu)
       Status: New => Confirmed

-- 
You received this bug notification because you are subscribed to the bug
report.
[https://bugs.launchpad.net/bugs/845066](https://bugs.launchpad.net/bugs/845066)

Title:
  Launch helper exited with unknown return code 127

---

### Post by PaulW2U on 2011-09-09
Interesting. I've seen this error just once on my Natty installation but its definitely gone from my Oneiric installation. Both are fully updated. 

Strange. :confused:

---

