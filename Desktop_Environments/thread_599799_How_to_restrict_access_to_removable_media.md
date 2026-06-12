---
title: "How to restrict access to removable media"
date: 2007-11-01
forum: Desktop Environments
---

### Post by giorgos07 on 2007-11-01
Hi,

I want certain users to access the removable media and others not. The user "user10" is not member of the group "plugdev" in my /etc/group. Nevertheless, "user10" can mount a removable disk such as a flash(usb) drive.

Part of my /etc/group says:
adm:x:4:user00
audio:x:29:user10
plugdev:x:46:haldaemon,user11,user12
haldaemon:x:110:
admin:x:114:user00

Can you please tell me what I should look for to solve the enigma?
Thanks
George

---

### Post by vbgunz on 2007-11-06
this is an excellent question. I too am very f****** curious as to how this is done??? You have no idea how long I've been trying to do exactly this!!!

BUMP!!!

---

