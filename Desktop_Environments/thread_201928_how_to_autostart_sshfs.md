---
title: "how to autostart sshfs"
date: 2006-06-22
forum: Desktop Environments
---

### Post by gaspedalo on 2006-06-22
Hi, I'd like to automount a ssh server via the FUSE sshfs command. I have a cronjob running every five minutes that will use the mounted folder, so it should be established before the cronjob gets running. 
I'm a Ubuntu newbie so I don't know what is the best way to do that.:-k

---

### Post by rowanparker on 2006-06-22
From the menu, System > Administration (could be Prefereces) > Sessions. You can enter any program/command in there to run on login.

---

### Post by gaspedalo on 2006-06-23
No, it should defenitely run before someone logs in. (It's a fileserver)

---

### Post by rowanparker on 2006-06-23
Try [BUM]("http://www.marzocca.net/linux/bum.html").

---

### Post by gaspedalo on 2006-06-23
BUM is nice, but it doesn't actually let me add a new script or command. It just lets me rearrange existing services and scripts and modules.

---

### Post by rowanparker on 2006-06-23
Oh yes, true, never noticed that before.

---

