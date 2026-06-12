---
title: "[SOLVED] Environment Variables.  Where are they stored?"
date: 2008-11-26
forum: Desktop Environments
---

### Post by roadrawts on 2008-11-26
Does anyone know where, in what file or files, the environment variables are stored? I need to restore them because I messed up my system and they are now gone.  I can't log on anymore because my home directory is on another drive.  I loaded a LiveCD so I can get to the filesystem.  /etc/fstab is correct but, for some reason, it can't find /home on the other drive.  So, I am concluding that the environment has been overwritten, or destroyed, and needs to be reset.

---

### Post by snova on 2008-11-26
Nowhere, exactly. Environment variables are copied from one program to another, propogating in a tree-like fashion to child processes.

Certain files contain defaults for some variables, some in /etc, some in your home directory. But there is no definitive list.

I doubt this has to do with environment variables.

How exactly did you mess up your system? What are the contents of /etc/fstab? And the output of this command, which displays the partition table:

```
sudo fdisk -l
```

Oh, and just to clarify, there is not supposed to be a directory called 'home' on the partition that holds it (I am assuming you have a / partition and a /home partition). You'll only find the contents of that folder, which will probably only be two directories: lost+found and your home directory, the name of which will be your username.

---

### Post by roadrawts on 2008-12-02
Thanks for the reply.  I did get the system back up and running.  The problem turned out to be with permissions on the directories.  Once I straightened that out, it all fell into place.  

Appreciate the help.

---

