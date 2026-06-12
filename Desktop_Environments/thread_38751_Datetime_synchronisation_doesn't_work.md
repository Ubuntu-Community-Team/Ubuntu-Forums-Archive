---
title: "Date/time synchronisation doesn't work"
date: 2005-06-01
forum: Desktop Environments
---

### Post by lewiz on 2005-06-01
Hi,

For some reason periodically synchronising my clock with Internet servers seems to make my clock run around 20 minutes too fast.  This is entirely regardless of the servers I use (I'm currently using the Manchester Computing (mcc.ac.uk) servers, which are about 15 minutes away).

Interestingly the one-time synchronise works fine.  I can't spot anything wrong with the ntpd.conf file.  Does anybody know what could be wrong?

---

### Post by stevenyu on 2005-06-02
Maybe double check the date/time setting in your BIOS next time you boot up the machine, maybe the battery need a replacement [-X

---

### Post by lewiz on 2005-06-02
[QUOTE=stevenyu]Maybe double check the date/time setting in your BIOS next time you boot up the machine, maybe the battery need a replacement [-X[/QUOTE]

Isn't that essentially the whole point of ntpd?  That it periodically synchronises with Internet servers to keep the local date/time in check?

---

