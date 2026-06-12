---
title: "mount.cifs as normal user?"
date: 2005-01-26
forum: Desktop Environments
---

### Post by neilmc on 2005-01-26
The man page says that you can use the setuid bit so that a normal user can mount a cifs share. I have done that with sudo chmod u+s mount.cifs and confirmed it in nautilus.

 It doesn't work though.

If I:

mount.cifs //192.168.1.111/sharenam  /mnt/mountedshare -o user=username,pass=password

I get: mount error: permission denied or not superuser and mount.cifs not installed SUID

If I put sudo before it it works. The resaon I don't want to use sudo is because I am getting the gnome session to mount it using a script for a particular user. I know I can have it mounted at boot using fstab, but I only want it mounted when this particular user logs in in gnome.

---

### Post by Ctrl+Alt+Del on 2007-11-04
you will have to chown the mountpoint with your user. It cannot mount without write permissions...

---

### Post by Meson on 2008-03-05
Ahh, they never tell you this in the guides.

---

### Post by DonQuichote on 2008-04-28
> **Ctrl+Alt+Del said:**
> you will have to chown the mountpoint with your user. It cannot mount without write permissions...

I had the problem that I had to add a "uid=<user name>" as well to /etc/fstab (where <user name> is the user that owns the mount point.

---

