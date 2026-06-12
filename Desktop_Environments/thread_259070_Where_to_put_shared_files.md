---
title: "Where to put shared files?"
date: 2006-09-16
forum: Desktop Environments
---

### Post by stevesmith on 2006-09-16
I want to have a directory that is shared between users on the same machine, for music, photos etc.  Is there a convention to where that should be?

Should I be setting up NFS for doing this, or just create a directory?

---

### Post by CatKiller on 2006-09-17
FWIW, I've got /data and /music directories accessible to all users, which are mount points for different partitions. Different drive, actually.

And if the users are all on the local machine, you don't need to do anything other than create directories. I suppose that if you put the directory somewhere obscure, you could put links in the users' home folders to be more convenient.

---

### Post by PvSinNL on 2006-09-17
I don't think there's a convention as to where to a shared directory should be. Personally, I'd just create a new directory under **/home** if I wanted it to be on the main partition.
Note that, by default, every user on a Ubuntu system has his/her own group. So, if you want to control access rights to some extent (other than simply making the directory world readable/writable), you need to create one or more groups and add users to them, depending on your specific requirements.

---

### Post by lamego on 2006-09-17
This could be done from the graphical manager but it's easier to copy & paste  to a terminal.
Open a terminal and:
```
# Create the "shared" group
sudo groupadd shared
# Add the users to the group
sudo adduser user1 shared
sudo adduser user2 shared
# Create the shared dir with the proper group owner/privileges
sudo mkdir /home/shared
sudo chgrp shared /home/shared
sudo chmod 770 /home/shared
```

---

### Post by stevesmith on 2006-09-17
Thanks!  I've gone for /home/shared.  I've created a symbolic link to it in each user's home directory, to make it even easier to get to.

Is there a way I can arrange it so that when I create a new user they will automatically already have a similar symbolic link in their home directory?

---

### Post by CatKiller on 2006-09-18
> **stevesmith said:**
> Is there a way I can arrange it so that when I create a new user they will automatically already have a similar symbolic link in their home directory?

I've not tried it, but /etc/adduser.conf (I found this by using **man adduser**) has a section that says

> # The SKEL variable specifies the directory containing "skeletal" user
# files; in other words, files such as a sample .profile that will be
# copied to the new user's home directory when it is created.
SKEL=/etc/skel

So if you add the link to the /etc/skel directory, or whatever it says in the equivalent section of your adduser.conf, then in principle every new user should have that link automagically appear.

Good luck, and don't forget to tell us if it works so that people searching the forum will know if this is a solution or not.

---

### Post by stevesmith on 2006-09-18
> **CatKiller said:**
> [...]add the link to the /etc/skel directory, or whatever it says in the equivalent section of your adduser.conf, then in principle every new user should have that link automagically appear.

Thanks!  That worked a treat.

---

### Post by CatKiller on 2006-09-19
> **stevesmith said:**
> Thanks!  That worked a treat.

Good stuff.

---

### Post by lorenzo on 2006-11-12
One more question: what about newly created files?

The above mentioned procedure works for existing files, but if my users add a file, the file is only modifiable by the owner and not by the group.

Is there a way to say that every file in the "shared" directory should belong to the "shared" group?

Many thanks,
Lorenzo

---

### Post by Steve Smith on 2006-12-22
> **lorenzo said:**
> Is there a way to say that every file in the "shared" directory should belong to the "shared" group?

Set the GID (group ID) bit of the shared directory.  For example, my shared directory is /home/shared,  In a terminal, type:
```

steve@blackbox:~$ cd /home
steve@blackbox:/home$ chmod g+s shared

```

If the shared directory is owned by root rather than you, remember to use 'sudo chmod'.  Make sure you aren't graphically browsing any directories when you do this, for some strange reason this seemed to confuse it when I just tried it!

This doesn't quite solve the problem though!  You really need folders and files to inherit permissions as well as inheriting the group,  I've found examples using umask, but since umask apparently inherits its settings from the process that runs it, the best advice I found was to set a chron job to run every minute to reset that - hardly ideal!

Anyone got a simpler idea?

---

