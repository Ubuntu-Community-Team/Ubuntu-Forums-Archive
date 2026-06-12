---
title: "SU Authentication failure - Help!!"
date: 2009-03-01
forum: General Help
---

### Post by andonato on 2009-03-01
I recently wanted to switch from my main user to another user (non-root) in the terminal, so I entered: 

```
su [user]
```

and entered the password for that user. It gave me the following:

```
su: Authentication failure
```

I tried it for root also (and yes, I did establish a root password), and that did not work either.

I know that this used to work, as I used to do it all the time. Here's the thing - I accidentally deleted my /bin directory and all subdirectories last week (bonehead move, don't ask...). I was able to restore /bin using a LiveUSB. Everything seems to be working again except this. Any ideas?

---

### Post by fragos on 2009-03-01
Ubuntu isn't set up to use "su". On the CLI use "sudo" in front of any command requiring root access as in "sudo command & parameters". If you with to use a GUI function as root "gksudo nautilus".

---

### Post by Old *ix Geek on 2009-03-01
> **fragos said:**
> Ubuntu isn't set up to use "su".I use su all the time. :confused:  There are times I don't want to be bothered with the restraints of sudo, so I **su -** and get my work done.

---

### Post by fragos on 2009-03-01
> **Old *ix Geek said:**
> I use su all the time. :confused:  There are times I don't want to be bothered with the restraints of sudo, so I **su -** and get my work done.

You may choose to that but you have some configuration to do with Ubuntu before su will work. There has been a geek pissing contest for years over su vs sudo but I won't argue the merits of either approach.

---

### Post by Xiong Chiamiov on 2009-03-01
You might have to setuid on the su executable.  That's my only guess.

---

### Post by heindsight on 2009-03-01
> **fragos said:**
> Ubuntu isn't set up to use "su". On the CLI use "sudo" in front of any command requiring root access as in "sudo command & parameters". If you with to use a GUI function as root "gksudo nautilus".

By default the root account is locked to prevent users from logging in as (or su'ing to) root.
However, using su to switch from one normal user account to another is perfectly acceptable
and should work without any problems.

> **andonato said:**
> I recently wanted to switch from my main user to another user (non-root) in the terminal, so I entered: 

```
su [user]
```

and entered the password for that user. It gave me the following:

```
su: Authentication failure
```

I tried it for root also (and yes, I did establish a root password), and that did not work either.

I know that this used to work, as I used to do it all the time. Here's the thing - I accidentally deleted my /bin directory and all subdirectories last week (bonehead move, don't ask...). I was able to restore /bin using a LiveUSB. Everything seems to be working again except this. Any ideas?

My guess is that the permissions of /bin/su are wrong.
su should be installed setuid root. Try doing:
```
sudo chmod 4755 /bin/su
```
and see if that makes a difference.

If your su permissions are wrong, it is very possible that other files in /bin also have incorrect permissions.
Do:
```
ls -l /bin
```and have a look at the permissions and ownership of all the files there, just to make sure.

--BEGIN EDIT--
Disclaimer, the permissions and ownerships for /bin files that I describe below
are as they are on my machine running Ubuntu 8.04.
It may be that you have other packages installed that placed other files with
different ownership/permission in /bin.
--END EDIT--

All files in /bin should be owned by user **root**. 
Also all files in /bin should belong to the group **root**,
except for /bin/fusermount which should belong to group **fuse**.

Also, all files (except symbolic links) in /bin should have mode ```
-rwxr-xr-x
```
**Except** for the following files (listed with their permissions):
```

/bin/fusermount  -rwsr-xr--
/bin/ping        -rwsr-xr-x
/bin/ping6       -rwsr-xr-x
/bin/mount       -rwsr-xr-x
/bin/umount      -rwsr-xr-x
/bin/su          -rwsr-xr-x
```
If these files have incorrect permissions you could use:
```
cd /bin
sudo chmod 4754 fusermount
sudo chmod 4755 ping ping6 mount umount su
```
to fix it.

Read the chmod manual
```
man chmod
``` for more info on permissions and how to set them.

---

### Post by andonato on 2009-03-02
> **heindsight said:**
> My guess is that the permissions of /bin/su are wrong.
su should be installed setuid root. Try doing:
```
sudo chmod 4755 /bin/su
```
and see if that makes a difference.


Thank you heindsight! I tried this and, voila, everything is working again. I also took your advice and investigated the permissions of the files in /bin. Everything looks good now after applying your fixes. Thanks!

---

