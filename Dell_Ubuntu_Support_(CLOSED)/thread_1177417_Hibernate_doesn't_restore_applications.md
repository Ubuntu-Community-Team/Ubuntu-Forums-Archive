---
title: "Hibernate doesn't restore applications"
date: 2009-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CaspianCanuck on 2009-06-03
Hello!

I am running Ubuntu 9.04 Jaunty 64-bit on my DELL Optiplex 960. I have 4 GB of RAM and a 8 GB swap partition. 

When I hibernate everything seems to work correctly, i.e. the system takes about 10-15 seconds to write some stuff on the disk and then shuts down, although the monitor light remains on.  However, when I restore from hibernate the OS just reloads as if from a regular reboot, not restoring the apps that were running before it went into hibernation.

I have installed the **hibernate** package but it didn't fix the problem.  Any ideas what might be wrong here?

---

### Post by CaspianCanuck on 2009-06-03
Forgot to mention that neither /var/log/kern.log nor /var/log/pm-suspend.log contain any errors or warnings or any other kind of messages that might hint at some problem.

---

### Post by pawnrocket on 2009-06-03
It sounds to me like it is another Jaunty bug. The only way to know for sure is to check the bug tracker. 

I to am eagerly awaiting an update.

---

### Post by pawnrocket on 2009-06-03
Tons of problems

[https://launchpad.net/+search?field.text=Hibernate]("https://launchpad.net/+search?field.text=Hibernate")

---

