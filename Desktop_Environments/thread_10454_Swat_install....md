---
title: "Swat install..."
date: 2005-01-07
forum: Desktop Environments
---

### Post by Dustin Wyatt on 2005-01-07
Tryin to install swat through Synaptic but I get a messages saying "Could not mark all packages for installation or upgrade  

swat:
  Depends: samba but 3.0.7-1ubuntu6.3 is to be installed"

I've searched for others having this problem and haven't been able to actually tell if anyone has solved this problem.  Any suggestions?

---

### Post by Cloudchaser on 2005-01-09
I had the same problem and would also be interested in finding a solution.

---

### Post by Dustin Wyatt on 2005-01-11
[QUOTE=Cloudchaser]I had the same problem and would also be interested in finding a solution.[/QUOTE]
 I take it this question has stumped every mighty linux guru here?  :D

---

### Post by Jæd on 2005-01-11
Apparantly... Would be handy as it makes installing samba shares easier...

---

### Post by NewbieNik on 2005-01-11
I get the same problem, but it seems pretty simple. The SWAT install is looking for the smaba package "3.0.7-1ubuntu6", but we have a newer version "3.0.7-1ubuntu6.3" installed.
I am currently looking for a newer SWAT release or an older Samba and will post my results here as and when!!


Happy hunting!

In the meantime I am happily using webmin. Try webmin.com for the latest version.

---

### Post by Jæd on 2005-01-11
Well I notice that there are two versions of samba:

3.0.7-1ubuntu6.3
3.0.7-1ubuntu6

Perhaps removing samaba and then "apt-get install" swat will select the correct one? Am at work so don't have time to try this at the moment...

---

### Post by Jæd on 2005-01-13
Solved by looking at [this thread]("http://www.ubuntuforums.org/showthread.php?t=8079&highlight=swat")

---

### Post by Dustin Wyatt on 2005-01-13
[QUOTE=Jæd]Solved by looking at [this thread]("http://www.ubuntuforums.org/showthread.php?t=8079&highlight=swat")[/QUOTE]
 Ahh...thank you.

Hopefullly this will be fixed "out of the box" in future releases.

---

