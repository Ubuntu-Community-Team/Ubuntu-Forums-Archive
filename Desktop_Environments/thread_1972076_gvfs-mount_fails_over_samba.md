---
title: "gvfs-mount fails over samba"
date: 2012-05-03
forum: Desktop Environments
---

### Post by Max-B on 2012-05-03
Hi,
I'm trying to connect to a samba share with the terminal using gvfs-mount on an Ubuntu Natty PC but I always got this error:

```
gvfs-mount smb://user@server.mydomain.com/share
Error mounting location: volume doesn't implement mount
```

Any suggestion?

Max-B

---

### Post by Morbius1 on 2012-05-03
You normally get that error when you don't have the following package installed:
```
sudo apt-get install gvfs-fuse
```And you haven't added yourself to the fuse group:
```
sudo gpasswd -a your_user_name fuse
```You need to logout and login again for the group add to take affect.

---

### Post by Max-B on 2012-05-03
Hi,
thanks for your reply.

gvfs-fuse is installed and I'm in the fuse group.
Of course the share exists and the server is online.

Max-B

---

### Post by Morbius1 on 2012-05-03
Is the base package installed: gvfs-backends

---

### Post by Max-B on 2012-05-03
Hi, and thanks again for the answer.
Yes, the base package is installed:

```
$ aptitude search gvfs
i   gvfs                            - userspace virtual filesystem - server     
i   gvfs-backends                   - userspace virtual filesystem - backends   
i   gvfs-bin                        - userspace virtual filesystem - binaries   
i   gvfs-fuse                       - userspace virtual filesystem - fuse server
p   libgvfscommon-dev               - userspace virtual filesystem - development
i   libgvfscommon0                  - userspace virtual filesystem - library    
p   xmms2-plugin-gvfs               - XMMS2 - gvfs plug-in  
```

---

### Post by Max-B on 2012-05-03
Hi again.
I found this useful tread: [http://ubuntuforums.org/showthread.php?t=1390955](http://ubuntuforums.org/showthread.php?t=1390955)

If I run the command after dbus-launch, gvfs-works works

```
dbus-launch bash
gvfs-mount smb://user@server.mydomain.com/share
```

This is not useful to me because, at the end, I would like to run a [**script**]("https://github.com/massimobarbieri/backup-tools") I have made, but probaply, if someone knows much more than me dbus-launch, is useful to understand which is the problem.

Max-B

---

### Post by Max-B on 2012-05-03
Hi!
I solved! The problem was that I tryed to run the command on a remote client.
Max-B

---

