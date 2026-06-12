---
title: "Access to folders"
date: 2006-06-24
forum: Desktop Environments
---

### Post by xenomorph99 on 2006-06-24
Hi,

I'm sure this is an easy one but...

If I add a user but I don't want them to be able to access anything other than their OWN home directory (and sub dirs), how do I do that? 

Also, by doing that, does it cause problems with respect to their being able to run applications?

Ta,
Xeno

---

### Post by ajgreeny on 2006-06-24
By default, only the first user, ie you, is able to be root using sudo, unless you have added them to the sudoers list in the file /etc/sudoers.

---

### Post by xenomorph99 on 2006-06-24
Hi,

I've not added them to the sudo list...I just added a user account.

However, if I log in 'as them', I can access the home dirs of 'other' users.

I'd quite like to partition it, like in Win XP, so that a user can only access their own 'home' folder.

Ta,
Xeno

---

### Post by ajgreeny on 2006-06-24
Surely this is because you know their passwords.  If that is not the case then you will need to make all the files in each separate home folder locked and not even readable by others.  I'm afraid I don't know how to do that, but I'll bet someone will tell you soon.  I presume you gave the other users a different password to you; I imagine they have to be, but again I do not know enough about user technicalities to say for certain as I am the sole user of my machine.

---

### Post by xenomorph99 on 2006-06-24
Hi,

I do know the passwords but the other users will not know the 'sudo' password so they shouldn't be able to break anything. I suspect it involves setting up a group permission for folders but I'm new to Linux and I'm certainly not sure what the best way to do this is.

Ta,
Xeno

---

### Post by aysiu on 2006-06-24
[This](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) is actually targeted at the opposite problem--allowing users to modify (and not just view) others' folders--but I'm sure the same principle would apply to restricting access as opposed to giving more access.

---

### Post by xenomorph99 on 2006-06-25
Hi,

Thanks for that.

I'm quite surprised about how much messing about their is to do this relatively simple task. I would have thought it would be 'built in' for a 'multi-user OS'

Oh well,

Ta,
Xeno

---

### Post by aysiu on 2006-06-25
Yeah, it's weird that way. You'd figure it would either be ultra-secure (no users can read or write each other's files) or ultra-lax (everyone can read/write each other's files). Instead, it's this weird middle ground where anyone can read anyone else's files but can't modify them...

---

### Post by Ramses de Norre on 2006-06-25
Can't you just make all home partitions non-executable for non-owners? Shouldn't that prevent other users from browsing them? 
I was quite confident it did but I can be mistaking.

---

### Post by aysiu on 2006-06-25
There are three kinds of permissions:

Read
Write
Execute

If you make a file or folder non-executable, that has nothing to do with whether it's readable or writeable.

---

### Post by Ramses de Norre on 2006-06-25
No, but doesn't mean non-executable not-browseable with a directory? I think I've read that somewhere but I haven't tested it yet (going to do so now;))

EDIT: it seems I was wrong with the executable thing, but just removing all permissions certainly restricts someone from viewing contents.
```
ramses@icarus:~$ mkdir -p test/test
ramses@icarus:~$ touch test/test/test
ramses@icarus:~$ chmod -x test/test/
ramses@icarus:~$ ls test/test/
test/test/test
ramses@icarus:~$ chmod -rw test/test/
ramses@icarus:~$ ls test/test/
ls: test/test/: Permission denied

```

---

### Post by aysiu on 2006-06-25
The problem with that is that it works for only the files you've manually changed permissions on. Once you create a new file, that will have the default permissions, which allows all other users to read the file.

---

### Post by Ramses de Norre on 2006-06-25
There you've got a point;) Too bad there is no simple way to set a default set of permissions for every file created in a certain directory without installing extra software..

---

