---
title: "Tip how to integrate Edgy Eft with Linux Samba server"
date: 2007-02-14
forum: Desktop Environments
---

### Post by johnwheez on 2007-02-14
Here is a little tip if you want your Ubuntu Desktop machine to connect to a Linux based Samba Server.

specify cifs as the filesystem type when running the mount command and not smbfs.

It seems cifs handles user permissions better and also allows transfers of files over 2 gigs.

This helped me get my Ubuntu Edgy Desktop system integrated in a demanding 3D Animation pipeline based on Maya.

--JW

---

