---
title: "With the new kernel it doesnt auto mount network drives"
date: 2005-12-25
forum: General Help
---

### Post by ashrack on 2005-12-25
I just compiled my own kernel. And with this new kernel it doesn't automaticly mount NETWORK drives during startup. It says network is unreachable. But when I reach desktop and then in terminal type "sudo mount -a"  it will mount the network drive.
I followed this guide:
[http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)

ps. If I boot up the machine from a previous kernel then the network drive is mounted during startup

---

### Post by ashrack on 2005-12-26
could anyone please help me

---

### Post by ashrack on 2005-12-27
Recompiled the kernel again and now it appears to work

---

### Post by ashrack on 2006-01-29
when patching the kernel with SWSUP2 I also had to install PORTMAP. For the mounting to work at boot up.
Anyone knows why? Since portmap is only needed for NFS shares IMO

---

