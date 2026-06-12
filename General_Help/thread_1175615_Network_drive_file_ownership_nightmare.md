---
title: "Network drive file ownership nightmare"
date: 2009-06-01
forum: General Help
---

### Post by jonboy99 on 2009-06-01
Hi folks, am using ubuntu dapper, and a synology NAS.

The problem is whenever I create a new file or folder in my NAS, the file immediately becomes owned by root.  I then cannot edit it.

I am mounting the NAS to a folder in my user home directory, using the following entry in fstab:

//192.168.1.16/NETfolder	/home/jon/synology cifs user,noauto,username=xxxxx,password=xxxxxx,iocharset=utf8,file_mode=0777,dir_mode=0777

Can anybody tell me a way round this?  If possible i'd like to have no ownership info for the files as I am accessing them from windows systems as well, but anyway that works will do.

At present i am having to mount the nas as root, which is obviously not good.

cheers
Jon

---

