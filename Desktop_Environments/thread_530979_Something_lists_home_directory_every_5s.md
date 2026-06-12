---
title: "Something lists home directory every 5s"
date: 2007-08-21
forum: Desktop Environments
---

### Post by itv on 2007-08-21
Hi,

I installed Feisty Fawn a while ago, and soon noticed that as soon as i start an X-session, something starts to read the contents of my home directory, and keeps doing this at every 5 seconds or so. My home dir is not local but on NFS, so this causes some extra network traffic. Nothing that the network couldn't handle, but it would be anyway nice to know what process is doing this, why, and can it be disabled?

---

### Post by itv on 2007-08-22
Ok, I found out that the culprit is probably the gnome-settings-daemon, which seems to be doing unsuccessful inotify_add_watch system calls at same intervals at which the listings are done...any ideas why, and how it could be fixed?

---

