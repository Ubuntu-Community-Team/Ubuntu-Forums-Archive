---
title: "Mount smbfs automatically when user logs in"
date: 2010-08-13
forum: Desktop Environments
---

### Post by iamroddo on 2010-08-13
I have a desktop that I want to use in a multiuser environment, that guests should be able to use. I want to be able to have users automatically mount network filesystems (smbfs) automatically when they log on, and only when they log on. Is this achievable in an uncomplicated way?

Alternatively I can add an entry to the fstab which would restrict access to the mounted shares according to the privilages of the logged in user.

At the moment I use the following entry to mount drives but it seems that this gives other users access also to these shares. How do I restrict this?

//bag-end/photo  /bag-end/photos  cifs  credentials=/home/xxx/.smbcredentials,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

I am running Ubuntu 10.4.

---

