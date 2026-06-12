---
title: "sudo chmod screwup"
date: 2009-02-04
forum: General Help
---

### Post by redscorpion69 on 2009-02-04
I was "playing" with some commands, and being a complete beginner i'm not sure what i did.

i typed sudo chmod 744 /usr/share/icons/*
and now some icons are gone, theres 'X' instead of them ;)
so how do i reverse this?

thx

---

### Post by redilyn on 2009-02-04
You are going to need to change the permissions back to drwxr-xr-x

```

sudo chmod 755 /usr/share/icons

```

That should do it I think

---

### Post by albinootje on 2009-02-04
> **redscorpion69 said:**
> I was "playing" with some commands, and being a complete beginner i'm not sure what i did.

i typed sudo chmod 744 /usr/share/icons/*
and now some icons are gone, theres 'X' instead of them ;)
so how do i reverse this?

Please run the following :
```

sudo su
find /usr/share/icons -type f -exec chmod 644 {} \;
find /usr/share/icons -type d -exec chmod 755 {} \;
exit

```

This is needed because a "sudo chmod 644 /usr/share/icons/*" will not solve your problems, because permissions for files and directories are unfortunately very different in general.

Read also :
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

And make sure to make regular and proper backups before continuing playing/experimenting around.

---

### Post by albinootje on 2009-02-04
> **redilyn said:**
> 
```

sudo chmod 755 /usr/share/icons

```

That should do it I think

The OP messed up permissions inside the /usr/share/icons/, your suggestion only concerns the permissions on the directory /usr/share/icons itself. 
It would be nicer to fix all the permissions on all files and directories.

Also files and directories have different permissions by default in Linux.
To be able to enter, read and write a directory in Linux (as owner), you will need at least 700 as permissions for a directory (or 755, the default).
But for files this should be 600 (for the owner) or the default 644, because 700 or 755 for a file makes it executable, which looks ugly imho and can be very annoying in some file managers when the files in question are not applications.

---

### Post by redscorpion69 on 2009-02-04
Thx all.

I typed 1st suggestion only sudo chmod 755 /usr/share/icons sudo chmod 755 /usr/share/icons and it worked perfect.
Do i still need to type the rest?

---

### Post by albinootje on 2009-02-04
> **redscorpion69 said:**
>  I typed 1st suggestion only sudo chmod 755 /usr/share/icons sudo chmod 755 /usr/share/icons and it worked perfect.

Good to know, now I realise that the 744 would not let your normal user into the /usr/share/icons directory, and a chmod 755 for that directory did help you to get back into that directory as normal user.
> 
Do i still need to type the rest?
Would be better if you did so, yes.

---

### Post by redilyn on 2009-02-04
Only if you want too :)

---

### Post by albinootje on 2009-02-04
I did a test by copying part of /usr/share/icons to /tmp

See here :
```

 ls -la /tmp/icons/
drwxr--r--  7 root root 4096 2008-07-02 12:29 Crux

```

As you can see the /tmp/icons/Crux directory still has 744 as permissions set.
Now I want to "cd" into the /tmp/icons/Crux as normal user :
```

cd /tmp/icons/Crux/
bash: cd: /tmp/icons/Crux/: Permission denied

```

To the OP, do you understand why this is ?
In other words, do you see why it makes sense to fix this problem properly ?

---

### Post by redscorpion69 on 2009-02-04
Yes i do. I don't know the syntax, but i know the underlying mechanism. I tought, just like redilyn suggested, that one command would take care of both dir/files permission. Anyway, now it's fixed. :)
Thx again for the help

---

