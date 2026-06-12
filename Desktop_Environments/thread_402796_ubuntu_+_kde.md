---
title: "ubuntu + kde"
date: 2007-04-06
forum: Desktop Environments
---

### Post by wecannotbesaved on 2007-04-06
I wanted to try kde so I used [this]("http://www.psychocats.net/ubuntu/kde") guide It worked.  I loged out and changed the session to kde.  Everything worked but I wasn't thrilled by it.  Then I logged into gnome, there was no way to connect to the internet, the connection icon says in gray "wired network" and nothing else.  kubuntu isn't connecting either anymore.  OS X still works though, so it's not a card problem.

I tried to uninstall kde with with
```
sudo aptitude remove kubuntu-desktop
```
but I get
```
bus error (core dumped).  0%
```

I am on a macbook, running dual boot, edgy eft and os x.  I'm sorry if this isn't enough information, just tell me what you need.

EDIT:  all of the package managers crash once opened.  When ever I try an apt or aptitude I get a bus error, described above, I get Internet with a wired network.

I really don't want to re-install everything...

---

### Post by wecannotbesaved on 2007-04-06
thanks for the help guys :roll: I got the internet working somehow.  But my package managers still crash and i can't do apt/aptitude.  These MAY be helpful someday

---

### Post by Tanker Bob on 2007-04-06
Try running "sudo aptitude update" from the shell command line.  That should rebuild the package list, which may solve your graphical package manager issues.

---

### Post by wecannotbesaved on 2007-04-06
I have tried, I get the bus error.

---

