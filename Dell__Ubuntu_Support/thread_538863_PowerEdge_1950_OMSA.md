---
title: "PowerEdge 1950 OMSA"
date: 2007-08-30
forum: Dell  Ubuntu Support
---

### Post by Scootin159 on 2007-08-30
I've got a Dell 1950 with the PERC RAID controller running Ubuntu 7.04 x64.  I had no problems with the install (even got vmware-server running without too much fuss), but need some way of monitoring the RAID 1 array as I will soon have no physical access to the machine.

Using [this](http://ubuntuforums.org/showpost.php?p=2336772&postcount=54) guide I was able to get (or so I thought) the dell OMSA utility installed, but now whenever I type "omreport" I get this:

```
$ omreport
Aborted
```

Anybody have any idea how to go about diagnosing this?

---

### Post by Scootin159 on 2007-08-30
or.... is there a better way to monitor the RAID 1 array besides openmanage?

---

### Post by Scootin159 on 2007-08-31
...

---

### Post by glee on 2007-09-04
Hey Scootin, I'd suggest you familiarise yourself with this thread:
[http://ubuntuforums.org/showthread.php?t=226114&page=6](http://ubuntuforums.org/showthread.php?t=226114&page=6)

You may also want to consider whether 7.04 is the best choice for your server environment. It has many known bugs and does not enjoy Long Term Support, as for example 6.06 LTS does...

Good Luck!

---

