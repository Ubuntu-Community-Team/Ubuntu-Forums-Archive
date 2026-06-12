---
title: "[SOLVED] ubuntu 8.1 wont boot after using gparted"
date: 2008-12-18
forum: General Help
---

### Post by mrbiggbrain on 2008-12-18
i used wubi to install 8.10 a few days ago, and today i decided i wanted to try to make linux from scratch so i shrank my main vista drive by 5.5GB, created a 512mb swap partition, and left the rest for when i started the project.

the shrink went fine (though took near 5 hours) i rebooted and vista fixed the disk as it should, and did a chkdsk on the main vista partiton. my assumption was everything went fine.

vista boots fine, no errors, but now when i choose ubuntu as my option i get an error message saying it cant boot, and gives an issue with grub pointing to the install point on windows...

HELP!

---

### Post by mrbiggbrain on 2008-12-18
i fixed the issue, i guess vista did some nasty stuff to my bootloader, had to repoint at the wubi installes bootloader

---

