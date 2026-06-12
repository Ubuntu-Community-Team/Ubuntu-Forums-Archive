---
title: "Cant mount c drive"
date: 2009-05-02
forum: General Help
---

### Post by chriszatch on 2009-05-02
I am able to mount the hp recovery partition, but i cant mount the c drive. It says that it is in use. It was shut down correctly last time i used it. 
(info= running a hp amd 64 with ubuntu 9.04 64 version. Dual booted with windows vista, which may change once i get the c drive mounted.....)l

---

### Post by otaker on 2009-05-02
you could try
  "mount /dev/sda1 /media/windows ntfs-3g force 0 0"
  if sda1 is your c drive
  else use "fdisk -l" to check what your c drive is

---

### Post by soro2005 on 2009-05-02
Check it for inconsistencies in Windows, either with chkdsk /f from a dos prompt, or with the utility that's somewhere in the disk info that opens from a right click menu.

---

