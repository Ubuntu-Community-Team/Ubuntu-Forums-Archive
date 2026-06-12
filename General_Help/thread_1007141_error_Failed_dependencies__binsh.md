---
title: "error: Failed dependencies:  /bin/sh"
date: 2008-12-10
forum: General Help
---

### Post by bobdobbs on 2008-12-10
I'm trying to install vmware.
Vmware for linux is offered in two formats: an rpm and a .bundle.
I downloaded the rpm, and installed rpm on my linux box.

This problem arises:

$: rpm -Uvh VMware-Workstation-6.5.1-126130.i386.rpm

error: Failed dependencies:
	/bin/sh is needed by VMware-Workstation-6.5.1-126130.i386

Absence of /sbin/sh thoroughly surprised me.

I created a softlink to bash:
ls -s /bin/sh /bin/bash

I ran rpm -Uvh again.
The same error message ocourred.

How can I fix this, and install vmware ?

Thanks.

---

### Post by geirha on 2008-12-10
Ubuntu does not use rpm, that's why you get that error (it can't find an installed rpm package with a posix shell). Try one of these methods: [https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

---

