---
title: "Ubuntu Newbie: I'm really confused"
date: 2009-05-07
forum: General Help
---

### Post by AmericanPrincess109 on 2009-05-07
I doubt this is the best section, but whatever:

I have a book that I've been writing on OpenOffice 2.4 and for some reason it keeps saying that I can't save because there's no room on the /.openoffice.org2/user/backup
well I went on that file (i guess you could call it) and I deleted everything in it. But even though it's completely empty it still says the same thing.
Like I said, I'm kinda new to Ubuntu and I have no idea what I'm doing.
:KS

---

### Post by taurus on 2009-05-07
Maybe you are running out of disk space!  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

p.s.  I assume you mean ~/.openoffice.org2/user/backup instead of /.openoffice.org2/user/backup since they are not the same thing.

---

### Post by nawitus on 2009-05-07
Try this to possibly get some disk space:
sudo apt-get autoremove

---

