---
title: "Unison not syncing folders starting with numbers"
date: 2009-04-28
forum: General Help
---

### Post by tcpipfddi on 2009-04-28
Hello all,

I have unison running on my laptop (ubuntu 9.04 jaunty) and a server (ubuntu 8.04 server). I set up the sync and everything went smooth until this day.

All of the sudden folders that start with a number are no longer synced. It is like unison does not see folders starting with a number like "1.Weekendtrip". If I rename it to "Weekendtrip" or to "A 1.Weekendtrip) Unison works fine.

Any ideas why unison behaves so strange?

My unison file:

root = /home/user
root = ssh://user@server

path = Documents

---

