---
title: "A Few Quick Questions"
date: 2009-03-12
forum: General Help
---

### Post by Drobbins on 2009-03-12
Hey All,

Just a quick question, i have just loaded Ubuntu back onto and old system of mine and have also loaded ClamAv however when i go to install the updated signatures (definitions) it says i must be root, how do i do this? 

Also i had a HDD connected to a OSX machine that i now want to use on Ubuntu how do i fully format it and use it with Ubuntu?

Many Thanks
Richard

---

### Post by DeMus on 2009-03-12
> **Drobbins said:**
> Hey All,

Just a quick question, i have just loaded Ubuntu back onto and old system of mine and have also loaded ClamAv however when i go to install the updated signatures (definitions) it says i must be root, how do i do this? 

Also i had a HDD connected to a OSX machine that i now want to use on Ubuntu how do i fully format it and use it with Ubuntu?

Many Thanks
Richard

To perform tasks as root you have to open a terminal: Application - Accessories - Terminal and type sudo ..... (whatever you want to do)
It will ask you for your password. Use your own user password here.

With the program Gparted you can delete, create and change partitions on a disk. It's in the standard repositories.

---

### Post by Drobbins on 2009-03-12
Brilliant :D

This command updates the signatures

$ sudo freshclam 

This command starts a scan 

$ sudo clamscan

I am installing gparted now so i will see what happens once that is done :-D

Many Thanks

---

