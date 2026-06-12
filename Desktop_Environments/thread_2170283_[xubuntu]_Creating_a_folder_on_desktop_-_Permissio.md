---
title: "[xubuntu] Creating a folder on desktop - Permission Denied"
date: 2013-08-25
forum: Desktop Environments
---

### Post by vikram_kapoor on 2013-08-25
I have many xubuntu computers but this one computer is not acting normal. I can't create a new folder on my desktop. It says **Permission Denied**. 
I also tried creating a directory from the terminal it says the same thing. Any specific reason ?

[IMG]http://img689.imageshack.us/img689/6810/xpje.png[/IMG]

---

### Post by GwL3eNC on 2013-08-25
Maybe there is realy something wrong with the permission of your desktop folder. Have you proved that for
example with ls -l to see the permissions the owner and group assignment. Both owner and group should
show your username. Access permission should look like drwxr-xr-x

Use chmod to change access permission, chown to set the owner and chgrp to set the group.

---

### Post by vikram_kapoor on 2013-08-26
> **GwL3eNC said:**
> Maybe there is realy something wrong with the permission of your desktop folder. Have you proved that for
example with ls -l to see the permissions the owner and group assignment. Both owner and group should
show your username. Access permission should look like drwxr-xr-x

Use chmod to change access permission, chown to set the owner and chgrp to set the group.

Thanks that worked. Don't understand how this happened in the first place though.

---

