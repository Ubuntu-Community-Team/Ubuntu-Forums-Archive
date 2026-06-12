---
title: "Remote into Windows computer at work?"
date: 2009-05-20
forum: General Help
---

### Post by javyn999 on 2009-05-20
Is this possible using Ubuntu as my operating system at home?  How would I go about it?  Thanks!

---

### Post by stoneheart on 2009-05-20
You can use rdesktop.  It's the equivalent of Remote Desktop on Windows.  However, most corporate IT departments usually make you open an encrypted connection to your work network first before you can talk to your work computer, and the methods they allow will vary. You'll need to check with IT at work if that's the case.

---

### Post by DGortze380 on 2009-05-20
It's possible if your work network allows it.

---

### Post by albinootje on 2009-05-20
> **javyn999 said:**
> Is this possible using Ubuntu as my operating system at home?  How would I go about it? 

Apart from rdesktop you can also use tsclient (Installed by default in Ubuntu).

rdesktop is a command-line tool, which you might not want, but it has a cool parameter option for the geometry where you can (apart from a resolution like e.g. 800x600) give in the amount in percentage. 

That can be very useful on a wide screen flat-screen I found out last week.

---

