---
title: "(yet) another automount problem"
date: 2006-09-16
forum: Desktop Environments
---

### Post by neill on 2006-09-16
hi

my samba server serves up various shares which i am trying to automount in ubuntu DD without joy

i have

auto.master
/home/user/data  /etc/auto.data  --ghost

auto.data
user -rw,soft,fstype=smbfs,user=user,password=password  ://server/sharename

in nautilus i get
/home/user/data/user folder (owned by root with 1200555 permissions) but no access - 'couldn't be found. perhaps it has been recently deleted'

i can browse and access the share in the normal way via places -> network servers etc etc

/etc/auto.smb server gives me
-fstype=smbfs \
         /share ://server/sharename

so the share is being shared out by the server

anyone see why it don't work - it's driving me nuts !!!! ](*,) 

previously i did try

mount -t cifs -o user=user,password=password //server/share /home/user/data

that mounted the share but with uid of 500 - the uid from the server

sadly my ubuntu uid is 1000 - so no access to those files there then !!

and before you suggest it - my server can't use smbfs with the uid set as the distro doesn't support smbfs, only cifs (although i may rebuild the ***** server with another dstro soon if i can't fix this :mad: )

any help very. very much appreciated

neill

---

