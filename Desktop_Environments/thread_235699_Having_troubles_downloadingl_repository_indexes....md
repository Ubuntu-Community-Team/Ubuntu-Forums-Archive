---
title: "Having troubles downloadingl repository indexes..."
date: 2006-08-13
forum: Desktop Environments
---

### Post by fwqhgads on 2006-08-13
When I try to install updates, or install anything (in this case, EasyUbuntu) I get this error: 

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to 200.114.140.74:3128 (200.114.140.74). - connect (111 Connection refused)
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:) Could not connect to 200.114.140.74:3128 (200.114.140.74). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to 200.114.140.74:3128 (200.114.140.74). - connect (111 Connection refused)

Anyone know what's going on?

---

### Post by ola on 2006-08-13
The first thing I would do when having problem with repositories would be to check what repositories you have in your repositories list.

You can find what repositories you are using in Synaptics (Look for repositories in the menu). If you are not using any special repositories you could probably remove the repositories in Synaptics and ad them again. (This is probably not the best way to "fix" it, but it have helped me some times.)

Good luck!

.o

---

### Post by WalmartSniperLX on 2006-08-13
> **ola said:**
> The first thing I would do when having problem with repositories would be to check what repositories you have in your repositories list.

You can find what repositories you are using in Synaptics (Look for repositories in the menu). If you are not using any special repositories you could probably remove the repositories in Synaptics and ad them again. (This is probably not the best way to "fix" it, but it have helped me some times.)

Good luck!

.o

Couldnt have said it better. If all else fails it doesnt hurt to uncheck em and reload, then check them all and reload.

In System/Administration/Software Properties

---

### Post by fwqhgads on 2006-08-13
I went in and unchecked all of the stuff in System >> Admin >> Software Porporties, but still get the 111 error, I can't connect to their server.

: /

---

### Post by drtvasudevan on 2006-08-13
having banged my head repeatedly at updating as it seems to be failing more often than work,
i found this in the archives:
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/)
is there any way i can keep up the updates from this?
how?
a little in detail please, i am a relative newbie.

---

### Post by fwqhgads on 2006-08-14
I'm a total n00b too

(bump)

---

