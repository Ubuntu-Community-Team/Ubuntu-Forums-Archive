---
title: "automatically create subfolders"
date: 2009-04-26
forum: General Help
---

### Post by R063R on 2009-04-26
Hello

I have a ubuntu 8.10 server that runs samba as a file server.

When I access the share from my XP machine it works fine, subfolders are automatically created when I save files in folders that does not exist yet.

When I run SSH to the file server and logon as root and run "touch subfolder/file.txt" in /root, I get "No such file or directory" becourse the subfolder does not exist, I want it to be created automatically.
I have tried in other directories as well with the same result.

Im running ext3 as filesystem.

Why is the subfolders automatically created ?
I get the same result in both ubuntu and centos..

Thanks

---

### Post by cmnorton on 2009-04-26
It sounds like you are mixing apples and oranges. How are you causing files and folders to be created on the share? Is it by dragging and dropping?

I don't believe Linux will automatically create a directory for you using the touch command. It can do this with the cp command (cp -r ). 

If this is under /root, you'll need to sudo mkdir /root/subfolder, and then sudo touch 
/root/subfolder/file.txt.

---

### Post by R063R on 2009-04-26
The source of my problem is that I have been using OneSwarm and when I download a group of files OneSwarm wants to create a folder in my download destination to put these files in.

But OneSwarm gets permission denied..

I get no problem when downloading single files with OneSwarm that does not create subfolders.

Some downloads starts if I manually create the subfolder that OneSwarm wants to put the files in.

The download destination folder is the samba share on my file server.

When using a local folder on the OneSwarm server I don't get this problem.

This is how my samba share is defined on the file server:
[files]
   comment = Files
   path = /var/fileSrvRoot/files
   writable = yes
   valid users = rogst anna lampsrv oneswarm
   force group = family
   create mask = 0775
   directory mask = 0775

this is how I mount the share on the OneSwarm server:
//172.16.1.8/files/oneswarm_downloads /mnt/filesrv_oneswarm_downloads smbfs username=oneswarm,password=*****,rw,users,uid=1000,gid=1000 0 0

uid 1000 is the user that is running OneSwarm

is there anything I am missing ?

---

### Post by cmnorton on 2009-04-26
Should the permissions be reversed? This is not a rhetorical question. I don't know how the Samba permissions work.

---

### Post by andrew.46 on 2009-04-27
Hi R063R,

> **R063R said:**
> 
When I run SSH to the file server and logon as root and run "touch subfolder/file.txt" in /root, I get "No such file or directory" becourse the subfolder does not exist, I want it to be created automatically.

Have you tried the -p option of mkdir?

> 
       -p, --parents
       no error if existing, make parent directories as needed


All the best,

Andrew

---

### Post by R063R on 2009-04-29
When I ran the command mkdir -p test/file.txt I got permission denied:(

the folder test was created, and the file.txt was not.

when I check the permissions on the oneswarm server i get
drwxr-xr-x 2 rogst rogst         0 2009-04-29 21:11 test

rogst is the uid=1000 and gid=1000 that I have specifed when I mounted the share.

When I check the same folder on the samba file server I get
drwxr-xr-x  2 oneswarm family      4096 2009-04-29 21:11 test

oneswarm is the user that the oneswarm server uses to mount the share.

There should be a write permission for the group family..

Should not "Directory mask = 0775" make the group get rwx ?

Even tried to use umask on the mount command but with no success

---

### Post by andrew.46 on 2009-04-29
Hi R063R,

> **R063R said:**
> When I ran the command mkdir -p test/file.txt I got permission denied:(

the folder test was created, and the file.txt was not.


Sorry I was no very clear :-). mkdir will only create the directory structure, you will still need to create the desired file.

Andrew

---

### Post by bodhi.zazen on 2009-04-29
When you connect via ssh your are using a bash shell.

You would need to write a wrapper script or function to do these things.

```
[ -x dir1/dir2/dir3 ] || mkdir -p dir1/dir2/dir3 && touch dir1/dir2/dir3/file.txt
```

---

