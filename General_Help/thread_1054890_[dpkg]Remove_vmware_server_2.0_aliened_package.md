---
title: "[dpkg]Remove vmware server 2.0 aliened package"
date: 2009-01-30
forum: General Help
---

### Post by mathmath51 on 2009-01-30
Hi, I used alien to convert vmware server 2.0 rpm to a .deb file.

The packaged installed but several functionality were not working.

So I tried to remove the package via :
apt-get remove
dpkg --force-all -r
dpkg --force-overwrite -i
dpkg --force-remove-reinstreq -P

And I have this error : 
Â*:
 le sous-processus pre-installation script a retourné une erreur de sortie d'état 1
[: 64: Illegal number: abort-upgrade
shift: 64: can't shift that many

dpkg*: erreur lors du nettoyage*:
 le sous-processus post-removal script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution*:
 vmware-server_2.0.0-122957_amd64.deb

The problem is that I can't now update my ubuntu because apt-get try to remove vmware-server first and fail.

I think it's a general dpkg problem when deb file are dirty.

Please, help me :)

---

### Post by Praetor77 on 2009-08-19
Have exactly the same problem, no way to remove the vmware-server even tried downlaoding and installing the correct .tar package through the script vmware comes with, but it errors when trying to uninstall the aliened version of vmware-server.

Tried forcing remove, dpkg, apt-get upgrade, etc...

Would really appreciate some help!!!

---

### Post by Praetor77 on 2009-08-20
Solved it, I finally made it by deleting /var/lib/dpkg/info/vmware-server.*

Then I installed the .tar.gz package available for download from vmware page. :)

---

### Post by hamidoo on 2010-06-14
wow! it worked for me too!
thx bro

---

