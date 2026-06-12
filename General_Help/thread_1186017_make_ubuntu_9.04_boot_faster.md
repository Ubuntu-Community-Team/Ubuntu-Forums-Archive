---
title: "make ubuntu 9.04 boot faster"
date: 2009-06-12
forum: General Help
---

### Post by dineshrathod2216 on 2009-06-12
Hi, i just switched from Windows to ubuntu and know nothing about ubuntu so please be patient. 
I calculated my reboot time in ubuntu and it was more than 65 seconds(which is very slow). But is there a way to make the boot process faster? 

P.S.: I have installed ubuntu using wubi installer. 

Please help, 
Dinesh.

---

### Post by jocampo on 2009-08-03
> **dineshrathod2216 said:**
> Hi, i just switched from Windows to ubuntu and know nothing about ubuntu so please be patient. 
I calculated my reboot time in ubuntu and it was more than 65 seconds(which is very slow). But is there a way to make the boot process faster? 

P.S.: I have installed ubuntu using wubi installer. 

Please help, 
Dinesh.

Wubi Installer does not provide same performance than installing Linux on its own partition; Ubuntu runs as a Windows application so you're not taking full advantage of Linux filesystem and features. 

Why you don't try a dual boot? is easy to setup via Live CD. Just be sure to backup your Windows data (photos, emails, etc) before start messing with partitions. You can post or ask here later if you have problems doing this.

Still, if you want to continue running Ubuntu that way try the following
-Disable services you're not using 
-Defrag your windows partition, where your Wubi resides. Heavily fragmented Windows partitions could affect your boot process.

---

