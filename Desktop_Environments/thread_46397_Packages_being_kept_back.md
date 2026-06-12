---
title: "Packages being kept back?"
date: 2005-07-04
forum: Desktop Environments
---

### Post by adamb10 on 2005-07-04
> 
adam@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.



Why are they being kept back?

---

### Post by doogie on 2005-07-04
I have the same two packages kept back, and don't have a problem. Firefox is currently at 1.0.4. I can't explain why (maybe someone else can), but I've adopted a "ain't broke, don't fix" mentality with this..

---

### Post by varunus on 2005-07-04
Are you guys using the "ubuntu-backports" repositories?  If so, then mozilla-firefox and mozilla-firefox-gnome-support are blank packages and can be held back, since the name of the package has changed to firefox and firefox-gnome-support.  If the message is annoying you, you can go ahead and open synaptic and just force the upgrade of those two packages; it won't do any harm.

---

