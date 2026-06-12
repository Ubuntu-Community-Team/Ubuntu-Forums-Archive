---
title: "synchronizing clock during bootup"
date: 2006-06-15
forum: Desktop Environments
---

### Post by qxrbuklp on 2006-06-15
I ve a standalone pc in which there is no internet connection. When Ubuntu boots up in that system, considerable time is wasted in 
'synchronizing clock to ntp.ubuntulinux.org'
as there is no internet connection, it finally says it failed.
 Is there a way to avoid this happening??

---

### Post by reztho on 2006-06-15
Open a terminal and write: sudo update-rc.d -f ntpdate remove

If you want to do it graphically just install BUM with Synaptic (or a proper packet manager) and disable ntpdate.

---

### Post by qxrbuklp on 2006-06-16
Thanks, i removed the ntp update service. Now the bootup time has decreased very much.

---

