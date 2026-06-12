---
title: "How do I make a link to a NAS file ?"
date: 2012-11-19
forum: Desktop Environments
---

### Post by PM47 on 2012-11-19
I have my work files in folders on a Network Storage Device (NAS). The NAS folders are mounted at startup through /etc/fstab as follows ...

//192.168.0.111/Drawings /media/nas_002/drawings cifs password= 0 0
etc.

I can open the folders through Nautilus and click on a file to open it in the associated application. If I try and make a link to the file, I get an error - 'Error making symbolic link: No such file or directory'. If I copy the file to the desktop (local hard drive) and make a link to it, it works fine.

How do I make a link to a file on the NAS such that clicking on it opens the NAS file in the associated application ?

Paul

---

### Post by LewisTM on 2012-11-19
File managers typically create a link in the current directory which you can move where you like. Problem is that Windows shares don't support the storage of symlinks so your are stuck.

The command line comes to the rescue. It creates a link directly at the desired location without trying to write to the NAS.
```
ln -s /media/nas_002/drawings/<file> /location/name_of_link
```
Cheers!

---

### Post by dannyboy79 on 2012-11-19
have you tried making a symbolic link?

---

### Post by PM47 on 2012-11-20
> **LewisTM said:**
> File managers typically create a link in the current directory which you can move where you like. Problem is that Windows shares don't support the storage of symlinks so your are stuck.

The command line comes to the rescue. It creates a link directly at the desired location without trying to write to the NAS.
```
ln -s /media/nas_002/drawings/<file> /location/name_of_link
```Cheers!

Many thanks, that works nicely :-)

Paul

---

### Post by dannyboy79 on 2012-11-20
> **PM47 said:**
> Many thanks, that works nicely :-)

Pauldon't forget to edit the original thread and mark it solved.

---

