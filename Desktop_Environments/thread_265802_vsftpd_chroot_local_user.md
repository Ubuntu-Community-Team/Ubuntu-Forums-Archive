---
title: "vsftpd: chroot_local_user"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Curtis_B on 2006-09-26
Hello, I'm just getting started with Dapper Drake. I installed vsftpd and added 1 user named 'artwork'. In the config file I set chroot_local_user = yes so that the artwork login cannot get to files beneath their /home dir. The problem is that I still want artwork to be able to create directories / read+ write files above their home folder. Currently logging in as artwork allows reading and writing only to the /home/artwork/ folder, but anything above that is not accessible/writeable. (Ex. trying to create a directory /home/artwork/newdir/ does work, but trying to write files to the newdir does not). 

Do I need to change ownership of /home/artwork to that user?

Do I need to add artwork to the 'admin' group?

Your help is much appreciated, Thanks. 

Curt

---

### Post by Bachstelze on 2006-09-26
By default vsftpd does not allow **any** write operation, by any user, in any directory. The first thing to do is changing the write_enable line in vsftpd.conf to YES.

---

### Post by Curtis_B on 2006-09-26
Yes, I had properly set write_enable originally. 

I think I understand my problem now. I had put a folder full of files in the artwork home directory as another user. Then, when I tried to access the files as 'artwork' via ftp it wasn't letting me. I ended up deleting everything and then re-uploading all files as 'artwork' and all is well. 

I think I just need to read up about users and ownership. I assumed files copied as another user would still be available to artwork.

Thanks

---

