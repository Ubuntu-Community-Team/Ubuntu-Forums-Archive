---
title: "genuine problem wiht grub"
date: 2009-06-01
forum: General Help
---

### Post by ayushjsh on 2009-06-01
I have a laptop, and i was having some problem configuring it as i just installed a UBUNTu over an existing fedora 10 installation. This laptop is not mine , and the partition table is something like this. 

/dev/sda1   ext3   label=/boot   flags=boot
/dev/sda2   lvm2                  flags=lvm
/dev/sda3   ext2
/dev/sda4   extended
/dev/sda5   ext3   mount point=/
/dev/sda6   swap



well this had fedora and the /sda4 was also a free drive like /sda3. i repartitioned it and installed ubuntu. but grub did not recognise fedora and i do not know what to add in my menu.lst so that i can get back the option of fedora back. the /sda partition has the vmlinuz files and GRUB folder of the installed fedora in /sda2. but since i have no idea about lvm format and how this could be corrected. Please help!!! i ahev tried adding all the regular additions to the grub , but they either say that the file is not found , or that i must give full file names in my menu.lst file ( as the previous install was such that name of entries in GRUB were relative to /boot. i am having a tough time here , please if someone has a slightest idea. HELP

---

### Post by YenTheFirst on 2009-06-01
Hello, ayushjsh.
I'm a bit confused about your setup. Are you trying to install ubuntu only? Install ubuntu and redhat side-by-side? Or something else?
Which partitions will the kernels be on for which distros?

Also, you might want to try out using a "Super Grub Disk" [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It has an assortment of features, including automagically fixing grub.

Also, try posting your current menu.lst, and maybe someone can see if there's a problem in it.

---

