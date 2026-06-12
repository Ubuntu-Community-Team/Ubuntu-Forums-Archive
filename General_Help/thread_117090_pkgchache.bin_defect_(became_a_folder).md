---
title: "pkgchache.bin defect (became a folder)"
date: 2006-01-14
forum: General Help
---

### Post by bjoern_kah on 2006-01-14
hello

today apt-get and synaptic stopped working with the following error message:

Reading package lists... Error!
E: Could not open file /var/cache/apt/pkgcache.bin - open (21 Is a directory)
E: The package lists or status file could not be parsed or opened.


/var/cache/apt/pkgcache.bin became a directory! it can't be deleted:

root@em05:/var/cache/apt # rm -rf pkgcache.bin/
rm: cannot remove directory `pkgcache.bin/': Directory not empty

but there isn't any file inside. there are even no . and .. inside.

any suggestion? is there another way to delete that folder/file? perhaps in the end it is better to make a complete reinstall. my ubuntu became quite slow..

thanks

bjoern

---

### Post by GeneralZod on 2006-01-14
"rmdir" will delete a directory - I believe apt will take care of restoring the package cache. If it still doesn't delete, then something is wrong and you may want to check your harddisk integrity  Also, there is almost no reason why the performance of Ubuntu should degrade with time, so a re-install shouldn't really help speed things up.

If you do need to reinstall, you might want to back up your /var/cache/apt/archives, to prevent you from having to re-download everything again.  Do you have your /home on a separate partition?

---

### Post by bjoern_kah on 2006-01-14
thanks. but i tried this rmdir either with the same result. next i will check the harddisk.

---

### Post by bjoern_kah on 2006-01-15
is there a way to check the harddisk while running the system or do i need a bootdisk?

---

