---
title: "New to Ubuntu"
date: 2006-01-30
forum: Desktop Environments
---

### Post by sinchronize on 2006-01-30
hi guys,

i have jus installed ubuntu linux.im new to it. please help me out in few things.

i want to mount my windows partitions on start up. 
i tried editing fstab file but im not able to edit it.
how do i do that?

can some1 get me a good pdf of linux for beginners?it will be very useful for me.


thanks a lot.

cya
sinchronize

---

### Post by BlakcTigers91 on 2006-01-30
[http://ubuntuguide.org/#remountfstabwithoutreboot](http://ubuntuguide.org/#remountfstabwithoutreboot)

That was reccomended, helped me out on ALOT of stuff.

---

### Post by sinchronize on 2006-01-30
hey

thanks for the link.

but the problem is im not able to edit the fstab file at all. it says i dont have permission.

also some1 suggest me a good website to download applications.

sinc

---

### Post by aysiu on 2006-01-30
Try Applications > Accessories > Terminal ```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

Or try Alt-F2 ```
gksudo nautilus
```

---

### Post by az on 2006-01-30
To edit a file that requires higher priviledges, you nede ot use sudo.

If you want to edit it using gedit, opena terminal and run

sudo gedit

You will be asked for you password and then you will be able to save the edited file.

As for applications, open Synaptic and pick what you want (System, Administration, Synaptic package manager.)

You will find about 13000 packages in the universe repository:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

