---
title: "Synaptic Online problems"
date: 2006-08-31
forum: Desktop Environments
---

### Post by df3n5 on 2006-08-31
I'm having problems with synaptic, when I go into it I get all of the packages that I have installed but none of the online ones. My internet is working with firefox so is it a problem with synaptic or something else? Thanks.

---

### Post by aysiu on 2006-09-01
Synaptic problems are actually best diagnosed by terminal commands. What's the output of this command? ```
sudo aptitude update && sudo aptitude install firefox
``` If all goes well, it should "hit" or "get" a bunch of online repositories and then tell you it's not installing Firefox because Firefox is already the newest version.

---

### Post by fast orange on 2006-09-01
I'm going to jump in with the same problem...i get a connection failed despite having internet access.
the errors all go on for the different repositories, but look exactly like these:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 195.248.90.54 80]

Are we having the same problem, any clues?

---

### Post by aysiu on 2006-09-01
It looks as if something is wrgon with the backports part of your repositories list.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, try again.

---

### Post by df3n5 on 2006-09-02
```
sudo aptitude update && sudo aptitude install firefox
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```
Doesn't make much sense to me. I tried installing extra repositories but got this error which doesn't look good to me.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
cp: cannot stat `/etc/apt/sources.list': No such file or directory

```
That doesn't look too good to me. Any ideas? Thanks for the help so far.

---

### Post by aysiu on 2006-09-02
For some mysterious reason, you don't have a sources.list. Just skip that step, then--all it's doing is creating a backup copy of your old sources.list.

Since you don't have one, you don't need to make a backup copy. Just go to the next step and paste in the new list.

---

### Post by df3n5 on 2006-09-03
Excellent thanks for the help, that sorted the problem out perfectly. Appreciate it.

---

