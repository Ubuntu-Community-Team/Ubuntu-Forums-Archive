---
title: "error in running cario-dock"
date: 2009-01-11
forum: General Help
---

### Post by jer-z on 2009-01-11
Hi,

Just want to know how to get rid of this error when I try to run cairo-dock..

> warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:885)  
  Attention : File is empty
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:566)  
  Attention : File is empty


Any suggestions will do... 

Thanks

---

### Post by binbash on 2009-01-11
did you try installing libthunar-vfs-1-2 ?

---

### Post by jer-z on 2009-01-11
I haven't...

Actually I did install cairo-dock before and it worked fine but when I've remove it and re install it again, I've encountered those error while running cairo-dock.

Also, Ive' just installed the libthunar-vfs-1-2 and yet I still having some error in running cairo-dock...

> warning :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:885)  
  Attention : File is empty
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:566)  
  Attention : File is empty


---

### Post by sendblink23 on 2009-01-11
> **jer-z said:**
> I haven't...

Actually I did install cairo-dock before and it worked fine but when I've remove it and re install it again, I've encountered those error while running cairo-dock.

Also, Ive' just installed the libthunar-vfs-1-2 and yet I still having some error in running cairo-dock...

I think probably you didn't completely remove it... before  Re installing cairo-dock

There is probably files still left from the old cairo-dock after removing it.

---

### Post by jer-z on 2009-01-12
I believe I did remove it all.. if not what am I supposed to do?.. and is there any way to get rid of the error?

Thanks!

---

### Post by binbash on 2009-01-12
> **jer-z said:**
> I believe I did remove it all.. if not what am I supposed to do?.. and is there any way to get rid of the error?

Thanks!

remove the cairo dock with purge : apt-get purge blabla

---

### Post by jer-z on 2009-01-14
yup.. you're right I haven't remove it all. ehe. tnx.

---

