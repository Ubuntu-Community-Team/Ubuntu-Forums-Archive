---
title: "problems running evolution over ssh"
date: 2009-01-26
forum: General Help
---

### Post by kseise on 2009-01-26
I have Intrepid running on my home desktop and Jaunty beta running on my laptop.  When I try to connect to the desktop to run Evolution over ssh, I get the following error.

> ** (evolution:22207): WARNING **: couldn't connect to dbus session bus: Failed to connect to socket /tmp/dbus-WjTinVQhHX: Connection refused


Can anybody help trouble shoot this?

---

### Post by e1mer on 2009-01-26
I sometimes find that I must type the command
```
xhosts +
``` prior to running ssh.

This allows your remote program to open windows
on your local system.

---

### Post by kseise on 2009-01-28
I get the command not found error.  It used to work on this computer without a problem.  The only thing that changed was that the desktop (server) was upgraded to 8.10.

---

### Post by kseise on 2009-01-28
I tried changing that to xhost + and got the following:

```
kseise@old-laptop:~$ xhost +
access control disabled, clients can connect from any host
```

I keep getting dbus errors.  This only happens with Evolution.  pan works fine, firefox works fine.  It is only Evolution.  Any ideas?

---

### Post by kseise on 2009-01-28
I GOT IT!!!!

I followed [this ]("http://ubuntuforums.org/showthread.php?t=879315")thread and changed the ownership of .dbus on the server /home/username to the username.  The .dbus file was apparently owned by root and username could not access it.  

Hope this helps anyone who had a similar issue.

---

