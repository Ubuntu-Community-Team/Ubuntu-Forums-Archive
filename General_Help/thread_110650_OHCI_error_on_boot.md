---
title: "OHCI error on boot"
date: 2005-12-31
forum: General Help
---

### Post by trivialpackets on 2005-12-31
Still trying to resolve this.  It kills my boot splash, and it's an error that repeats that first part of it 3 times.  It's one of the first things that is running in the start up process, and makes reference to usb takeover failed.  Any ideas?  Possibly something in the kernel that's not needed or missing something that is?  A recompile perhaps?

---

### Post by trivialpackets on 2006-01-03
No ideas?  

I'm going to give Dapper a try since I'm not in class anyways.  Hopefully I can get this straightened out before classes start again.

---

### Post by trivialpackets on 2006-01-06
So, I tried Dapper, and it worked, at least the boot splash, too many other little things will keep me from using it for good, but I do find some solace in knowing that the issue will be corrected soon.

I really hate being the only one posting in my own thread, but if there is anyone else with this issue, or have experienced anything similar, I have some questions.  Is it a problem in the kernel?  And, where it is working for me without problem in Dapper, but there are some other issues, would an upgrade of just the kernel from dapper possibly fix the issue?  Also, if I do this, when I choose the dapper kernel, it only installs one package and does not install the other kernel packages that install when I installed one from the Breezy Package for linux-k7.  Any ideas or anyone who has gone through this?

---

### Post by Slade Winstone on 2007-02-12
Hi, I'm running Edgy, 2.6.17-11-generic, and found a strange, kinda, partial work-around, for this problem:
[http://ubuntuforums.org/showthread.php?p=2143128]("http://ubuntuforums.org/showthread.php?p=2143128")

---

