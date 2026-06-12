---
title: "VUBUNTU or Where to post intrest in new 3rd Party Ubuntu Projects"
date: 2006-06-07
forum: Forum Feedback &amp; Help
---

### Post by lah on 2006-06-07
The 'main'  3rd Party Ubuntu Projects forum seams cloesed. I have hard to find where to post this... any pointers?

VUBUNTU - Ubuntu for Linux VServer guests.

Ubuntu already works prety well with [https://wiki.ubuntu.com/VServer](https://wiki.ubuntu.com/VServer) but while upgrading a VServer guest from hoary to dapper i had some problem. Most solved but it could be alot easier.

Problem:

A VServer guest don't need hardware suport and usaly dont have the right to do stuff like mount, creating devices etc.

Some of these pakages is esential, or for other reason pulled in by a dist-upgrade. Faling to install becose of trying to mount or creating devices. That make dpkg/apt belive the system is broken and the upgrade halts.

Solution:

Probably a mix of:

Provide a vserver-guest pakage that fake provide som non needed pakages while actuly removing them.

Fix some dependencys... posably a vserver version of all metapakages.

Alter/replace some pakages: A syslog not depending on klogd, parts of initscripts is probably neede, part is not and harmfull, Rebuild bind.

Make a VServer guest ubuntu that just works and rocks!

Some work on the VServer host might be needed to... The VServer-copy script use legasy config, but the rest of the tool use the 'new' config (I have a raw replacment - but it need work).

Dokumentation. The ubuntu dokumentation on it's VServer features is a bit thin.

Propaganda - VServer is cool teknology, should be markeded that ubuntu handels them well.... but, first we probably shuld handle them even better :-)

Mainly I'm intrested in finding peers intressted in such project.... And where to post such querry.

Thanks /LaH

---

### Post by ubuntu-geek on 2006-06-07
Sure drop me a PM with all the details and we can set it up.

---

### Post by lah on 2006-06-07
OK. I was mainly intrested to find out if ther is more people intresting in this and discus howe to best solv it and *then* possably form a project.

But I will investigate it a bit thurder anyway, and might come back with a PM.

Thanks for the reply /LaH

---

