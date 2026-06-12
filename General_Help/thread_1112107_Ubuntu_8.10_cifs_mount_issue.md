---
title: "Ubuntu 8.10 cifs mount issue"
date: 2009-03-31
forum: General Help
---

### Post by pmbsa on 2009-03-31
Hi, I have a problem with a cifs mount that I cant get my head around and I am hoping somebody can point out the obvious mistake. 

I have added the following line to my /etc/fstab

\\192.168.1.254\public\music  /media/musicserver  cifs  user,uid=1000,file_mode=0777,dir_mode=0777,guest,nounix,gid=1000  0  0

the mount works fine, I can rename any of the files that are already there (permissions look fine) but I cannot add files and I cannot do anything with the files at all, if I try I get a location not found error.

I am tearing my hair out so I would appreciate any assistance it this point (I have never had this before). The installation is pretty new, basically just installed and run the latest updates. I have installed samba correctly as far as I can tell as well.

thanks
Paul

---

### Post by pmbsa on 2009-04-08
Nobody!?

---

