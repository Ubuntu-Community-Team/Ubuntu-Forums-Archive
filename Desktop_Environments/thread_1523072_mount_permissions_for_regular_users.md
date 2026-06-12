---
title: "mount permissions for regular users"
date: 2010-07-03
forum: Desktop Environments
---

### Post by kkaldroma on 2010-07-03
I am (now) running 10.04 and have run into the problem of boot hangs when having network boot locations in the fstab. 
I have written a script to mount everything I want on startup which has speed up boot and stopped the freezing problem.

The new problem is that I have to be a super user to run the script properly because lowly users can't mount using smbfs.

I hate having to run a scripts with  "echo MYPASSWORD | sudo S" all over it so I'm hoping for another solution.

Additional:
The mount location is owned by user trying to mount.
The mount source is windows XP and Ubuntu 9.10 using Samba (zero local security NAS box).

code: ```
mount.smbfs //{ip}/{folder}/ /mnt/{location} -o pass={Space} 
```everything in "{}" is a description, {Space} is used because when using SMBFS a pass is needed.
:

Any ideas (even terrible ones) are welcome. So far my Googlefu has turned up a bunch of wrong answers.

Anyone


Bueller?

---

### Post by quixote on 2010-07-05
I ran into a vaguely similar problem using virtualbox.  I don't know if it will work for smbfs.  For vbox, I have to add ```
uid=1000,gid=1000
``` to the mount options (1000 being my regular user and group number).  That gives the only regular user on my vbox system permission to mount and own a shared dir.  I'm not sure what the syntax would be if you wanted to add all ordinary users (i.e. all equal to or greater than 1000).  You could try it with 1000, and then if it does what you want, see how to generalize it.

---

### Post by kkaldroma on 2010-07-08
Adding the user UID fixed the permissions problem but I would still like to give users mount privileges.

I did it back in 9.10 by chown(ing) the mount locations but that doesn't seam to do it for 10.04

---

### Post by quixote on 2010-07-08
I thought adding "user" to the mount options does that.  Doesn't that work for you?  There's some subtle difference between that and "users" as an option, but I think they both allow ordinary users to mount and unmount filesystems.  So, for example, your fstab entry could look like this:```
mount.smbfs //{ip}/{folder}/ /mnt/{location} -o pass={Space},uid=1000,gid=1000,users
```Again, I'm not sure how smbfs wants things, so maybe that doesn't work in your case.  "man mount" doesn't give a lot of info about smbfs.

---

### Post by kkaldroma on 2010-07-09
Even with the 'users' tag I still get a mount permissions error.
As a regular user I am not permitted to mount.

output
```
mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```I have read through the mount.cifs man page but it doesn't explain how to do what I do.

---

### Post by quixote on 2010-07-09
It's probably some intricacy of smbfs that's tripping us up.  Maybe somebody will get in here who knows the answer? :D  

I think mount.cifs refers to another type of filesystem.  Have you tried mount.smbfs?  If there is such a thing.  Also, maybe your user id isn't 1000??  Open a terminal and type "id *username*" to see what it is.

---

### Post by quixote on 2010-07-09
Now that I look more closely at my own list of groups, I see that I'm a member of "120(sambashare)".  Maybe your user isn't a member of the necessary group?  I know that hung me up with vbox for a while, fwiw.

---

