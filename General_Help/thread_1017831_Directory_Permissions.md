---
title: "Directory Permissions"
date: 2008-12-21
forum: General Help
---

### Post by Computermoss on 2008-12-21
Hey All,

Have a slight problem with a drive that i just mounted.  I can read about half of the directories on it, however, the Documents and Music directory's are locked.  They are read only permission, so they do not allow me to view or grab the backups that are in them.

I have tried chown, and chmod commands (chown paul Documents, chmod -R 0777 Documents...) and nothing works to unlock them.

They are on a HD that is from a mac system I believe (10.5.5).  Where do I start? :)

Thanks,
--Paul

---

### Post by Computermoss on 2008-12-21
basically i need to change the whole file system from read only i think... just dont know how to.  advice is appreciated.

---

### Post by gettinoriginal on 2008-12-21
You do not say what your specific flavor of linux is, but this advice is if you have Ubuntu.  Alt F2 will open a box, into that box, type: "gksu nautilus" (without the quotes)  this will open your file browser with root privileges.  Go to the file you want, select properties, permissions, and change it there.    :P

---

### Post by wolfen69 on 2008-12-21
```
sudo chown -R user:user /dev/sda
```
of course replace user with your name and instead of sda, replace with your drive. you can find that out by ```
sudo fdisk -l
```

---

### Post by Computermoss on 2008-12-21
ok the alt f2 did not work.  gave me an error when trying to change permissions.  said it was a read only drive and i could not change it from that either.

my terminal commands did not give me an error.  but it still did not give me ownership of drive.  still read only file system.

what now?

PS:  I am ubuntu 8.10

---

### Post by Computermoss on 2008-12-21
oh and one more thing.  the root file browser DID allow me to actually enter the locked directories.  it did not however, allow me to copy all the data over or change file system permissions.  just wanted to clarify that.

---

### Post by wolfen69 on 2008-12-21
did you try my commands? and then reboot?

---

### Post by Computermoss on 2008-12-21
did not reboot... sry

doing that now.

---

### Post by Computermoss on 2008-12-21
reboot did nothing.  still the same deal.

---

### Post by Computermoss on 2008-12-21
bump

---

### Post by Computermoss on 2008-12-21
the hard drive i am trying to mount is an HFS+ file system... if that helps

---

### Post by Computermoss on 2008-12-21
i solved my problem.  booted into a hackintosh cd image... opend disk utility... repaired permissions.  I also did some terminal work (chmod, etc)

Works great now.

---

