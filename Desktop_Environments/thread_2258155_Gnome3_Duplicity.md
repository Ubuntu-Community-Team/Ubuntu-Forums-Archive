---
title: "Gnome3 Duplicity"
date: 2014-12-25
forum: Desktop Environments
---

### Post by Archer920 on 2014-12-25
Hi! I just installed Ubuntu 14.10 (the Gnome3 version). 

Whenever I launch Duplicity to configure automatic backups, I get this message:

archer920@14:~$ gnome-control-center deja-dup
GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I really don't even know where to begin with something like this? Any suggestions?

---

### Post by phidia on 2014-12-26
You could issue > sudo apt-get update and > sudo apt-get upgrade and see if that resolves your problem.

There is a bug at launchpad that refers to that error message-you can look at the thread about that [here]("https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1289807").

---

