---
title: "Booting the system"
date: 2008-12-05
forum: General Help
---

### Post by superpiccione on 2008-12-05
Dear all,

I have dowloaded Xubuntu with the idea of using it on a home laptop which is running very slowly with windows. I wanted, however, to try it first throught the CD demo version. The problem is that the CD did not want to boot so I asked it to facilitate it (believe this was the right way to phrase it).

I think it meant it would install some files on my PC, though not the entire system. So now when I start up the machine, I get the duel boot screen asking whether I want to start Windows or Xubuntu. If I choose the latter he promts me if I want to install it all, run the demo from the CD....

Basically I want to remove this dual choice, I want this machine to always run Windows, Xubuntu was not meant for her!

I just need basic instructions (I'm no super expert but I can navigate through a pc...) to remove the dual-boot choice...

many thanks

S

---

### Post by Existentialist on 2008-12-15
In order to restore the windows boot loader; boot from your windows cd and enter the recovery counsel.  Type the command:

fdisk /mbr

This will get rid of the grub boot loader.  I am not sure what files xubuntu wrote to your disk, or if it created a partition so I can't be of more help then that.  Sorry.

---

### Post by theozzlives on 2008-12-15
> **Existentialist said:**
> In order to restore the windows boot loader; boot from your windows cd and enter the recovery counsel.  Type the command:

fdisk /mbr

This will get rid of the grub boot loader.  I am not sure what files xubuntu wrote to your disk, or if it created a partition so I can't be of more help then that.  Sorry.

go to start>control panel>administrative tasks>.computer management>disk manager, it'll tell your partition info there

---

