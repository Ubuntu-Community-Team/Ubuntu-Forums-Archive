---
title: "SCP and write privilages"
date: 2009-03-16
forum: General Help
---

### Post by malfist on 2009-03-16
I have a folder in /var/log that I need to write to it remotely and I'm using a C# port of SCP to record the logs of a C# port of Rsync. Is there a way to make the directory only writable by SCP and root? I know an SSH connection has the privileges of the user that logged in (unless it's been chroot jailed), but I really don't want to login to the backup server as root just to write log files, that seems kinda dangerous. 

How would you do it?

---

### Post by bodhi.zazen on 2009-03-16
I would copy the file as a user, then ssh in and move it with sudo.

If this is inconvenient, I would use keys and allow root to log in with a key only. This does NOT require you to set a root password.

---

