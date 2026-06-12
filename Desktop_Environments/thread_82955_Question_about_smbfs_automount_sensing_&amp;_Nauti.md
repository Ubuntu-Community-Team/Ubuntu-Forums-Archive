---
title: "Question about smbfs automount sensing &amp; Nautilus"
date: 2005-10-27
forum: Desktop Environments
---

### Post by ULffuntu on 2005-10-27
Hello,

I've managed to automount my networked NTFS drives in fstab, but I've noticed something odd. If I open the networked drive in Nautilus my Network Monitor Applet in the panel flashes every second. I noticed if I switched to another physical directory that it would still flash alot. So I tried to fix this by including a max TTL in the fstab and rebooting.

//MCP/d        /media/mcpd  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777,ttl=100000   0       0

This seemed to fix the flash when I'm on a physical directory, but not when nautilus is on the NTFS drive itself (still the same). Can this automount sensing be tweaked to calm down? Thanks in advance.

---

