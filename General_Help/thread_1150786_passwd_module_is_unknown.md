---
title: "passwd: module is unknown?"
date: 2009-05-06
forum: General Help
---

### Post by NiceGuy12 on 2009-05-06
Hi everyone,

I am unable to login to my ubuntu server. My password contnues to fail all of a sudden (and I know it is correct).

Regardless, I decided to boot from a livecd, mount my root partition .. chroot then attempt to change update my password, this is what is produced:
```
root@livecd:/etc/pam.d# passwd <username>
passwd: Module is unknown
passwd: password unchanged
```
Any Ideas?

---

### Post by NiceGuy12 on 2009-05-07
Hi everyone,

As it turns out I had to simply reset pam ... two options ethier from the LiveCD or from booting into (Recovery Mode) kernel from grub
```
pam_tally --reset --user <username>
```
Only allowed so many failed attempts
Thanks and hope that helps someone else

---

### Post by vevel on 2010-04-23
That didn't work for me, however, forcing a rewrite of PAM configuration worked:

$ sudo pam-auth-update --force

---

### Post by Nuukee on 2011-01-11
I had the same problem with my Ubuntu 10.10 - the last advice from vevel helped!! Thanks a lot!

---

