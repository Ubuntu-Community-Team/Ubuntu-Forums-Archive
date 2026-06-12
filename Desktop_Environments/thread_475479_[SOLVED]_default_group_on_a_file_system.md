---
title: "[SOLVED] default group on a file system"
date: 2007-06-16
forum: Desktop Environments
---

### Post by tedius on 2007-06-16
I have a partition where I store all my music.  All my uses have permission to write new tracks there, but when they do the owner appears as user:user.  Is there some way that I can force any new files to automaticly become pare of the music group.  So when a use adds a new track the owner will appear as user:music.

I can do it using chgrp, but I'm sure that I have seen something that I can add to the fstab file to get this to happen.

Thanks

---

### Post by llamakc on 2007-06-16
You can set the GID bit.


**Directory Set Group ID**

  If the setgid bit on a directory entry is set, files in that directory will have the group ownership as the directory, instead of than the group of the user that created the file. 

This attribute is helpful when several users need access to certain files. If the users work in a directory with the setgid attribute set then any files created in the directory by any of the users will have the permission of the group. For example, the administrator can create a group called spcprj and add the users Kathy and Mark to the group spcprj. The directory spcprjdir can be created with the set GID bit set and Kathy and Mark although in different primary groups can work in the directory and have full access to all files in that directory, but still not be able to access files in each other's primary group.

The following command will set the GID bit on a directory:  
  chmod g+s spcprjdir 
  The directory listing of the directory "spcprjdir": 
  drwxrwsr-x     2     kathy     spcprj     1674     Sep 17 1999     spcprjdir 
  The "s'' in place of the execute bit in the group permissions causes all files written to the directory "spcprjdir" to belong to the group "spcprj" . 


from [http://www.cohttp://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.htmlmptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.cohttp://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.htmlmptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

