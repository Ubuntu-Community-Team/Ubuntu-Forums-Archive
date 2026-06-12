---
title: "permission problem"
date: 2008-11-10
forum: Desktop Environments
---

### Post by HINDI on 2008-11-10
Hi

i can't allow others users to use 777 permission commands .
chmod 777 fdisk
su normaluser
fdisk-l
fdisk:you must be root to do that
but i think that i don't have to use suders file while I've already changed the command permission to allow the others to use it.
but i can use ls command although it has less permission 755

i thought that changing the permission of any executable to rwx for the others will allow any one to execute that executable .
is it something related to SElinux .

also what is the interpretation of r for the executable ?
what if the permission of the executable was only --x--x--x ,will that make a difference ?

---

