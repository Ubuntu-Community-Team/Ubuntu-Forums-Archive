---
title: "See the windows network"
date: 2009-03-01
forum: General Help
---

### Post by Phil Binner on 2009-03-01
Wireless networking is good but I can't see the windows network. I have tried to configure samba, but I do not have write permissions in the /etc/samba directory, and I can't find out how to get them. This is my Ubuntu box and the others are my windows boxes; there are no network administrators blocking me.

I have set the share options so that the rest of the network can see me, and can also write to the Ubuntu box, though this causes some issues. The share options on the windows machines allow them to see each other. Where do I go from here.

Help

:confused:

---

### Post by Iowan on 2009-03-01
I hope the short answer to your problem is "sudo".  To edit Samba's configuration file, use one of these:```
sudo nano /etc/samba/smb.conf
``` ```
gksudo gedit /etc/samba/smb.conf
``` It may also be possible to use one of the Application text editors as "root" but I haven't tried.

---

