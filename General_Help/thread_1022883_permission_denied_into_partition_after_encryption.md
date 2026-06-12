---
title: "permission denied into partition after encryption"
date: 2008-12-27
forum: General Help
---

### Post by basicxman on 2008-12-27
I wanted to password protect a partition so I followed this tutorial: [http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

The procedure seemed to work fine so I restarted the computer.  On boot it asked me for my password into /dev/sda3 I entered it and it continued to boot.  Now that I am in the system I get 'permission denied' on any attempts to add, move, delete files.  Help?

Thanks -basicxman

---

### Post by itix on 2008-12-29
The guide says that the encryption is for root file systems which is the reason why you can't use it with the normal user. Root, or super user as it is called, (sudo = super user do) is the only user that can use the file system.

If you really wan't to use it, you can press Alt + F2 and type *sudo nautilus* and use the filesystem throuh the super user.

I have no idea if this works since I have no idea what the encryption does, but you can change the ownership of things with the *chown* command. That whould in your case be *sudo chown [your username] -R /media/[the name of your partition]*. As I said however, I can't garatuee that it'll work since it is encrypted.

---

