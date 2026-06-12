---
title: "update problem keep getting &quot;must manually run 'dpkg --configure - a' to fix...&quot;"
date: 2009-01-25
forum: General Help
---

### Post by CaimSasori on 2009-01-25
Okay so I have 12 available updates.
And I have for a while.
and I need to update. But I can't.

Every time I try, I get an error message saying:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

And I try to run "dpkg --configure -a" in the terminal and it says that I don't have the superuser privelages (note: I'm the only user on the computer)

And I also tried to install a few new games from add/remove and I got the same message

What do I do? (By the way I have Ubuntu Intrepid 8.10)

---

### Post by oldos2er on 2009-01-25
```
sudo dpkg --configure -a
```

---

### Post by taurus on 2009-01-25
Close the Add/Remove window first.  Then from a terminal, run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Use the same password that you log in with.

---

### Post by CaimSasori on 2009-01-25
I feel so stupid...i'm such a noob...

---

