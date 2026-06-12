---
title: "I cannot update!"
date: 2009-05-15
forum: General Help
---

### Post by Rytron on 2009-05-15
Hi.
On my secondary PC I installed a package before, I don't remember which one. The package was not installed correctly.
I cannot update! Here is the error message:
```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```
What must I do to remedy this? 
Thanks.

---

### Post by kpkeerthi on 2009-05-15
Open Synaptic and check **History** from the menu.

---

### Post by gettinoriginal on 2009-05-15
If the above does not fix things:
Also, please note the last error, "cache open".  That means you already have a package manager open.  You can only have one (terminal, synaptic,
or add/remove) open.  If it is still a problem, then try this:

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by Rytron on 2009-05-16
> **gettinoriginal said:**
> If the above does not fix things:
Also, please note the last error, "cache open".  That means you already have a package manager open.  You can only have one (terminal, synaptic,
or add/remove) open.  If it is still a problem, then try this:

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

Hi. I tried your advice but it did not solve the problem.

However I did manage to sort it out by going to Software Sources. I unchecked restricted & multiverse. Also I hit restore defaults button under the Authentication tab. Then I clicked close & reload. Done.

:D

---

