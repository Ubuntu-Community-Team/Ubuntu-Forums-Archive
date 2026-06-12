---
title: "Nautilus reading tar files"
date: 2006-07-03
forum: Desktop Environments
---

### Post by queenorych on 2006-07-03
I would like to open a tar file for reading across a smb share.  File-roller seems to just be a nice gui wrapper around the none gnome-vfs aware tar/bzip/gzip/etc..  Now gnome-vfs appears to support reading tar files, but i can't get nautilus to read them.  For instance if i try to open the test.tar file on my desktop, with the uri I think should work '/home/mike/Desktop/test.tar#tar', I get an error 'Couldn't display file'.  

Does Nutilus have the ability to read a tar.  if so how.

Thanks

---

### Post by Jagot on 2006-07-03
I don't think so - archive manager handles .tar files in Ubuntu.

---

### Post by queenorych on 2006-07-04
gnome-vfs should be able to open a tar file from a smbmount.  I even see /usr/lib/gnome-vfs-2.0/modules/libtar.so .  So the functionality is there, but how do I utilize it!

---

