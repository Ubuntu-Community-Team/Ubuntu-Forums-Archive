---
title: "Booting raid1 after failure"
date: 2009-06-01
forum: General Help
---

### Post by crimsondr on 2009-06-01
Hi all,

I want to setup a new server with boot on software raid1.  I've been testing this using VMWare.

I created a virtual with 4 hard drives.  sda1 and sdb1 raid1 for /boot.  I then remove sdb and replace with a new sdb.  Add it back to the array and it rebuilds.  Then I remove sda.  Now the system will no longer boot.  Shouldn't sdb take over?

If starting from scratch and I just remove sda and try to boot it works fine.  It's only after sdb is rebuilt and sda is removed that it can no longer boot.

What am I missing to make this work?

Thanks.

---

