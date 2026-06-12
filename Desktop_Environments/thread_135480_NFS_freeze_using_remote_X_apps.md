---
title: "NFS freeze using remote X apps"
date: 2006-02-23
forum: Desktop Environments
---

### Post by lduperval on 2006-02-23
Hi,

I have a wireless setup with a desktop and a laptop. The desktop is set up as an NFS server. The laptop is a client. When I move files using mv or cp, everything works great. However, if an application on the laptop tries to access data on the desktop, then my NFS connection hangs.

For example, if I use mpg123 on the laptop to play a file on my desktop, NFS hangs. If I use qiv on the laptop to view a picture that resides on the desktop, NFS hangs.

Does anyone know why this happens? Better yet, does anyone have an idea how to fix this problem?

Thanks!

L

---

### Post by joshuapurcell on 2006-02-23
I'm not exactly sure why you would have problems with NFS (since I don't use it much), but there is possibly a workaround to your problem. You can log into your desktop through ssh using and run X applications using this command:```
ssh -X user@host whateverXCommandYouLike
```user = username on desktop
host = hostname of desktop
You can use firefox, eog, xmms, and the like. I haven't used it for applications like totem, but I don't see what it wouldn't work for watching movies as well.

---

### Post by lduperval on 2006-02-24
Hmmm... Will the sound output be on the local machine or the remote machine? I suspect it will be on the remote machine. But I'll try it nevertheless.

Thanks,

L

---

### Post by joshuapurcell on 2006-02-24
[QUOTE=lduperval]Hmmm... Will the sound output be on the local machine or the remote machine? I suspect it will be on the remote machine. But I'll try it nevertheless.

Thanks,

L[/QUOTE]
The program will run on your laptop (sound, video, everything).

---

