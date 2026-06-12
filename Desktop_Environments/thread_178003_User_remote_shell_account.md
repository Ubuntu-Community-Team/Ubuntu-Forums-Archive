---
title: "User remote shell account?"
date: 2006-05-17
forum: Desktop Environments
---

### Post by Swad on 2006-05-17
In all my linux years, there is one thing I have never really delved into.  I would like to setup a locked down environment for a friend of mine to ssh into my machine and to load up and IRC client on the shell.  I would like to keep him locked into his home directory and in his own environment.  I assume some of this would involve chroot and the like.  Are there any good documents / HOWTOs on setting up such an environment in Ubuntu to allow access to specific programs for a friend and keep him locked into his own environment?

Thanks.

EDIT: I have all of the SSH stuff taken care of as I use that regularly--I just need to know what I need to do to properly setup restricted shell access for him.

---

### Post by Ramses de Norre on 2006-05-17
Can't you just add a user and let him log in with that user? Give him a small home folder and no permissions on anything outside that folder.

---

### Post by Swad on 2006-05-17
It's something I have never done before, so I don't know.  If I can just create a normal user account and they will by default be locked out--so be it.  I'll give it a shot here.  I think part of me, though, was aiming for a setup similar to how some Internet shell accounts are where a user is locked into an environment that is seperate from the rest of the system.

---

### Post by Mujaheiden on 2006-05-22
I'm trying to set up the same thing. I want to lock my guest user into his home, and i believe i made a guest group, and a guest account, but he's still able to browse around, in my mounts, etc.
Should I change the group of all my files? this sounds a bit scary... a HowTo would be nice indeed...

---

### Post by jones_jj on 2006-05-23
I don't know of a way to lock an account to a certain area in the file structure.  But browsing/reading and actually executing is different.  If a user doesn't have root access there is very little that user will be able to do besides just browse around the file structure.

---

