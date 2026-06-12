---
title: "(13 Permission Denied)"
date: 2009-05-06
forum: General Help
---

### Post by OxentroT on 2009-05-06
I have been having this problem for the past two weeks. I have even re-installed multiple times and I am still getting the same errors when trying to install some apps:

> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

and under root:

> clyde@sleitht:~$ sudo apt-get install kmd
[sudo] password for clyde: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



and sometimes I get this:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

---

### Post by atomizer on 2009-05-06
what happens when you do ```
sudo dpkg --configure -a
```

I think that some installation has been interrupted a few weeks ago, so there is still a "lock" file open.

---

### Post by OxentroT on 2009-05-07
thankyou:)

---

