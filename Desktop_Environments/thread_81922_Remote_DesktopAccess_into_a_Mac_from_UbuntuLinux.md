---
title: "Remote Desktop/Access into a Mac from Ubuntu/Linux"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Iggie on 2005-10-25
Is there any way to RD into a Mac from Ubuntu?  

Thanks,

--

Iggie

---

### Post by kalin on 2005-10-25
Installing a vnc server on the Mac should do the job, something like [OSXvnc]("http://www.redstonesoftware.com/vnc.html")

---

### Post by Iggie on 2005-10-25
Is there anyway to do it outside of VNC?  I'm talking about 20 or so Macs.

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=Iggie]Is there anyway to do it outside of VNC?  I'm talking about 20 or so Macs.[/QUOTE]
Not sure what your criteria is, but you can ssh into Macs to perform batch updates, etc.

---

### Post by Iggie on 2005-10-26
Updating software, installing new software, etc., would be the criteria.

---

### Post by cwaldbieser on 2005-10-26
[QUOTE=Iggie]Updating software, installing new software, etc., would be the criteria.[/QUOTE]
I'd try ssh then if I could.  Probably a lot easier to script a bunch of installs from the command line than to go out to every machine and run a .dmg.

---

