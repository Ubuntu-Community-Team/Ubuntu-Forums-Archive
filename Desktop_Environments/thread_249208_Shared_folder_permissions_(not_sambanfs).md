---
title: "Shared folder permissions (not samba/nfs)"
date: 2006-09-02
forum: Desktop Environments
---

### Post by svasie on 2006-09-02
I have two different users (my wife and me) in my home computer, and, apart from each user's home directory, I want to have a shared folder (call it /home/sharedfolder) where both users can read/write every file/folder, and where file/folder permissions are keept when any of both users creates/modifies files and folders.

I know i can create a cron job reseting file permissions every time i want, but i think this is not a clean solution.

Sorry for my english.

---

### Post by qwertz on 2006-09-02
You can either give access/read/write rights to anyone:

chmod a+rwx /mnt/sharedfolder

Or if you want to restrict access to those two users, then make both users members of the same group (say "users"; if there are not already). Then

chgrp users /mnt/sharedfolder
chmod g+rwx /mnt/sharedfolder

---

### Post by svasie on 2006-09-02
Giving rwx to the group is not a solution. If one of the users creates a new file or a folder, that file will be created with the default group of than user so the file probably wont be writable to the other user.

I need that every file/folder created in the shared folder by any of the users is owned by group "users" and has rw permissions for that group.

---

### Post by pertti on 2006-09-30
> **svasie said:**
> Giving rwx to the group is not a solution. If one of the users creates a new file or a folder, that file will be created with the default group of than user so the file probably wont be writable to the other user.

I need that every file/folder created in the shared folder by any of the users is owned by group "users" and has rw permissions for that group.

I'm looking forward to this, too. So far I've found how to automatically set the group ownership of the files created on a directory. If you want that all the files created on /home/shared belong to the same group 'users', first you have to set the group ownership of that folder to 'users', and then set the gid bit:

chgrp users /home/shared
chmod +s /home/shared

But this is only half of the solution, because, despite being owned by the 'users' group, all files will be created with the default privileges, which usually means no writing for group members :(. So we need some way to automatically set g+w permissions on every file created there.

Anybody knows a clean solution to this?

---

### Post by jpmorelli on 2006-10-04
I´m just looking for the same thing, I think there is have to be a solution for this, or no one´s shares files with others users when they use the same computer but differents accounts? ](*,)

---

### Post by jpmorelli on 2006-10-04
If this helps...

[http://www.ubuntuforums.org/showthread.php?t=194388&highlight=shared+folder+same+computer]("http://www.ubuntuforums.org/showthread.php?t=194388&highlight=shared+folder+same+computer")

---

### Post by chalex on 2006-10-04
I think what you want is the following:

Make userA belong to groupA.  Make userB belong to groupB.  Make both users belong to groupC.  Make a new directory which is owned by groupC.

Next, set the system default umask in /etc/profile to 002 instead of 022.  Type "default umask" into google to find out more, or here's a link I chose for you from the results: [http://www.linuxsecurity.com/content/view/117255/](http://www.linuxsecurity.com/content/view/117255/)

That should do it.

---

