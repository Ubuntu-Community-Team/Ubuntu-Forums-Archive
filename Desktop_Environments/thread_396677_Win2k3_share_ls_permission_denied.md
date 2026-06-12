---
title: "Win2k3 share ls permission denied"
date: 2007-03-29
forum: Desktop Environments
---

### Post by 00coday on 2007-03-29
I am having a problem with permissions on a windoze 2003 share on a server recently added to active directory.  Before the move to AD, I was able to mount shares on the windoze box with no problem.  Now the mount statement executes fine, but when I do an ls of the mount I get a permission denied error and the permissions for the mounts look like:

?--------- ? ?    ?       ?                ? /mnt/dvicweb/http
?--------- ? ?    ?       ?                ? /mnt/dvicweb/weblogs

The mount statement is as follows:

mount //155.7.145.84/weblogs /mnt/dvicweb/weblogs -o username="<domain>\<user>",password='<password>',dmask=777,fmask=777

The weblogs share has everybody/full control permissions, so anybody should have access to it. The user I am using for the mount is a domain admin, so there shouldn't be any problems with permissions there.

  I also followed the HowTo at [http://doc.gwos.org/index.php/Active_Directory_Authentification](http://doc.gwos.org/index.php/Active_Directory_Authentification)   for using AD authentication and joining the Ubuntu box to the AD domain.

Any thoughts... ](*,)

---

