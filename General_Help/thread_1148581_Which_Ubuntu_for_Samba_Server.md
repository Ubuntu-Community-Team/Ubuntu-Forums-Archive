---
title: "Which Ubuntu for Samba Server?"
date: 2009-05-04
forum: General Help
---

### Post by ScaryBob on 2009-05-04
I have a small home Samba server that is currently running Mandriva desktop. I want to switch to Ubuntu but not sure which version to use.

Details:
1. Samba is used to store backups and media files for 2 home desktop PCs and 2 HTPCs.
2. Samba share is a RAID5 array using MDADM.
3. HTPCs currently use direct file access on Samba share.
4. CPU is AMD 4850e Athlon X2 with 2 GB RAM.
5. Server may also be used as a TV server with MythTV or other media server software in the near future.
6. Remote administration is desired, from both Windows XP and Ubuntu workstations using both the shell and desktop.

Which would be the best choice:
1. Desktop or server edition?
2. 32 bit or 64 bit?

Which remote administration tool would be best? (I currently use VNC but security is an issue.)

TIA for all replies.

---

### Post by Kai-vana on 2009-05-04
I would suggest Desktop and 32bit, the only real difference between desktop and server is desktop comes with X-server and Gnome pre installed, also it looks like you processor is only 32bit so the 64bit OS would not work.
VNC is still a good remote administration tool and you can secure it buy tunnelling the VNC connection through SSH.

---

