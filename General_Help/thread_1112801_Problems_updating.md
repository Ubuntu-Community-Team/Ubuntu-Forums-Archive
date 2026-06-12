---
title: "Problems updating"
date: 2009-04-01
forum: General Help
---

### Post by artilluer on 2009-04-01
So the comp froze on me and I held the power button until it shut down but I was in the middle of an up date and now I can't get the update to work because it says manually run dpkg --configure -a but when I enter in sudo dpkg --configure -a i get a message that says dpkg: parse error, in file `/var/lib/dpkg/updates/0012' near line 1:
 newline in field name `, please help and since I am new to linux, easy to understand wording would be helpful thanks.:p

---

### Post by dcstar on 2009-04-01
> **artilluer said:**
> So the comp froze on me and I held the power button until it shut down but I was in the middle of an up date and now I can't get the update to work because it says manually run dpkg --configure -a but when I enter in sudo dpkg --configure -a i get a message that says dpkg: parse error, in file `/var/lib/dpkg/updates/0012' near line 1:
 newline in field name `, please help and since I am new to linux, easy to understand wording would be helpful thanks.:p

That directory is empty on my system, so this might work:
```
sudo rm -r /var/lib/dpkg/updates/*
sudo dpkg --configure -a
```

---

### Post by IceBadger on 2009-04-01
artilluer, I would not remove folders as your first effort to fix the problem.  If you were in the middle of an update you may need them (depending on how far you got).

Try running the following first:
```

sudo apt-get clean all
sudo dpkg --configure -a

```

If that does not resolve the problem, you may need to remove as dcstar suggests and see what happens.

**EDIT:**  I found this thread to back up what I suggested.  Seams like the same problem:  [http://www.linuxforums.org/forum/ubuntu-help/138465-dpkg-configure.html#post667473](http://www.linuxforums.org/forum/ubuntu-help/138465-dpkg-configure.html#post667473)

---

### Post by artilluer on 2009-04-01
thanks guys I tried icebadgers way but it didn't work but when i tried the dcstar's way it worked so thanks alot for the quick responses and help :p:p:p:p=D>:mrgreen:\\:D/

---

