---
title: "CIFS share mount-dismount issues"
date: 2010-07-11
forum: Desktop Environments
---

### Post by feffer on 2010-07-11
I use a network device as a fileserver to 3 local machines. It should mount automatically when a machine boots and unmount properly at shutdown, but I get inconsistent behavior depending on which machine is involved. One machine running debian sid behaves properly. An Ubuntu machine mounts the share properly at boot, but hangs up at shutdown. After a minute or so, the "CIFS server" dies and then the machine will shutdown or reboot. The 3rd machine, running Kubuntu will not mount the share at boot or let go of it at shutdown. All have the same fstab line:```
# CIFS share for Sheeva backups etc
//sheeva/data-srv  /media/data-srv  cifs  auto,defaults,rw,credentials=/path-to-file
```I've done considerable searching, and tried several things, but haven't resolved this. AFAIK, all three machines are set up similarly at least as far as samba goes, but obviously something is different. Any thoughts about how to troubleshoot this?

thx,
feffer

---

