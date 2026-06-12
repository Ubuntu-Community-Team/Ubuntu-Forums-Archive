---
title: "Really strange problem with file permissions"
date: 2010-10-10
forum: Desktop Environments
---

### Post by cinohpa on 2010-10-10
I mount a partition to a directory and ls -liah tells me that everyone has read/write/execute permissions on the whole thing, but I try to save a file into the partition and I get an access denied error. 

First of all this doesn't make sense because ls is telling me I do have access. 

Then it gets weirder.

I run sudo chown -R me:me directory. The command exits without error, but then when I go and look at the directory again with ls, it still shows up as owned by root and I still have the same problem.

This is particularly strange because I am still able to change permissions normally in the operating system filesystem. It just won't work on the mounted partition. 

Thanks.

---

### Post by cinohpa on 2010-10-10
Solved!

The reason chown couldn't help me change my file permissions is because I was trying to change permissions on an ntfs partition. 

I fixed this by umounting the partition and then 

```

sudo mount -o uid=user,gid=group /dev/thingtomount /place/to/mount

```

What is strange is that I had been using a directory on the ntfs partition as the dl folder for firefox for a while and only today something finally decided not to let firefox write downloads to the directory. This is the problem that made me notice the strange behavior with chown.

---

