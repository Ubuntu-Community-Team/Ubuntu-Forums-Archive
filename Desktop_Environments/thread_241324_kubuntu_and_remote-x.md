---
title: "kubuntu and remote-x"
date: 2006-08-22
forum: Desktop Environments
---

### Post by sutterp on 2006-08-22
I need to access a kubuntu workstation via remote-x. Some clients here do not have vnc installed, so remote-x is the only option I have.

What do I need to do in kubuntu to get this working. I could figure out how to do it in ubuntu, but in kubuntu I have drawn a blank.

Enable is set to true in [Xdmcp] in /etc/kde3/kdm/kdmrc, both hosts have dns entries.

In other distros, there is an /etc/X11/xdm/xdm-conf where one normally has to enable DisplayManager. 

The only result I get at the moment is 

Manager unwilling - Host unwilling

Thanks

Peter

---

