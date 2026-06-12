---
title: "Mounting an XP share using cifs and user / other rw restrictions."
date: 2009-04-27
forum: General Help
---

### Post by uncle-c on 2009-04-27
Good morning all. A little problem which has been bugging me all weekend.
Some background first. I have a directory on my XP machine, "tmp," which is set to share. I have set advanced permissions so any attempt to access  this, and subsequent write operations on any files, will require password authentication. This works swimmingly. I have made a subdirectory to the /mnt directory on my Ubuntu box called "xp" onto which the xp share is mounted. I have set permissions to xp which allows only me to rwx :

```
unclec@unclec-desktop:/mnt$ ls -al
total 16
drwxr-xr-x  4 root   root   4096 2009-04-18 15:39 .
drwxr-xr-x 20 root   root   4096 2009-04-06 18:05 ..
drwxr-xr-x  2 root   root   4096 2009-04-18 15:39 floppy
drwxr-x---  2 unclec unclec 4096 2009-04-16 15:10 xp
unclec@unclec-desktop:/mnt$ 

```

I mount the xp share from ubuntu like such :

```

unclec@unclec-desktop:/mnt$ sudo mount -t cifs //xxx.xxx.xxx.xxx/tmp -o user=unclec,password=******** /mnt/xp

```

This is all well and good. I have my XP share , c:/tmp, mounted and I can acccess, r/w all files. However, as I mounted using the "sudo" command, the /mnt/xp directory has now assumed different permissions :

```
unclec@unclec-desktop:/mnt$ ls -al
total 16
drwxr-xr-x  4 root   root   4096 2009-04-18 15:39 .
drwxr-xr-x 20 root   root   4096 2009-04-06 18:05 ..
drwxr-xr-x  2 root   root   4096 2009-04-18 15:39 floppy
drwxrwxrwx  2 root   root 4096 2009-04-16 15:10 xp
unclec@unclec-desktop:/mnt$ 
```

As you can see "xp" is now world readable and writeable and nothing can stop any other user on the system from manipulating xp share while this cifs session is open. In addition other users can issue the mount or cat /etc/mtab command and see this :

```
newuser@newuser-desktop:/home $ mount
/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
....... lines omitted
gvfs-fuse-daemon on /home/unclec/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=unclec)
//xxx.xxx.xxx.xxx/tmp on /mnt/xp type cifs (rw,user=unclec,password=*********)
newuser@newuser-desktop:/home $ 

```

You can clearly see the situation and the problem herein. I  not only need the xp share to be accessible i.e. rw,  by no one BUT myself. I also want to avoid my username and password being shown when casual users issue the mount or cat /etc/mtab command. I had a look at a "credentials" file but this did not work on 8.10.

Cheers,
UC

---

### Post by uncle-c on 2009-04-27
Ok folks I've solved part of the problem, the visibility of the username and password is still for all to see.
Here is the fstab entry pointing to  my xp share :

```

//xxx.xxx.xxx.xxx/tmp /mnt/xp cifs noauto,user=unclec,password=*****,uid=unclec,file_mode=0770,dir_mode=0770  0   0

```

This mounts the xp share on "/mnt/xp" with only root and unclec having permissions to rwx to files and directories. Unfortunately, I cannot get the "credentials=/path/to/credentials.file" part to work when I alter the fstab accordingly. 
```
//xxx.xxx.xxx.xxx/tmp /mnt/xp cifs noauto,credentials=/path/to/credentials.file,uid=unclec,file_mode=0770,dir_mode=0770  0   0
```

I've set username, password and file permissions correctly but I still cannot get it going.
I checked any error messages using "demsg | tail " and I get :

CIFS VFS: No username specified
CIFS VFS : cifs_mount failed w/return code = -22

Like I said both username and password are in the credentials file. I'm flummoxed.


cheers,
uc

---

### Post by uncle-c on 2009-04-28
Just a quick note to say that the credentials problem has now been solved. For the directive to work one **MUST** have **SMBFS** installed.
Here is the command line entry :

```


$ sudo mount -t cifs //***.***.***.***/tmp -o credentials=/path/to/credentials.file,uid=unclec,file_mode=0770,dir_mode=0770 /mnt/xp


```

The above will mount the password protected XP share ( ***.***.***.***/tmp )onto mount point /mnt/xp without being prompted for your password. When mounted the xp directeory and all subdirectories + files will be owned by user unclec. All file and directory  permissions will be 770 i.e rwxrwx---. As a result no users except unclec and root will be able to cd to /mnt/xp while it is mounted.
**fstab** entry :
```


//***.***.***.***/tmp /mnt/xp  cifs  noauto,credentials=/path/to/credentials.file,uid=unclec,file_mode=0770,dir_mode=0770  0   0

```

The fstab entry contains  **noauto** so the windows share will not be automatically mounted at boot up and will have to be mounted explicitly using the **sudo mount** command.

```
$ sudo mount //***.***.***.***/tmp 
```

---

