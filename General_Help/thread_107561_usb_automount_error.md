---
title: "usb automount error"
date: 2005-12-23
forum: General Help
---

### Post by jocke1s on 2005-12-23
Hi all,

Just did a fresh install of kubuntu breezy.

When I attach my usb memory stick I get
an error

media:/sdf1:

It says file or catalogue doesn't exist.

Is there an easy solution or should I dig deeper?

Regards
Joakim

---

### Post by sourc3 on 2005-12-23
I had the same problem... solved by manually add the device to /etc/fstab.

---

### Post by mlomker on 2005-12-23
If you type **dmesg** after inserting it you can verify what the device name is.  Are you getting this after clicking on the desktop icon?

---

### Post by sabitha on 2005-12-23
have u try to install the new "pmount". try looking on this forums about that, maybe it can fix that ;)

---

### Post by robert114 on 2005-12-26
Are you using Ubuntu 5.10 and have you updated your system?
I've had simular problems with KDE on 5.04 and some of the 5.10 preview versions. But these problems were solved on the official release of Ubuntu 5.10 

On 5.04 I've solved the problem by manually adding the device on /etc/fstab . Unfortunately I don't know exactly what i've added in the config file (/etc/fstab).

---

