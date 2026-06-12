---
title: "Create User In Terminal"
date: 2005-10-21
forum: Desktop Environments
---

### Post by karuptdata on 2005-10-21
IS it at all possible to create a new user from the terminal command prompt and if so how??THANKS

---

### Post by mlgg on 2005-10-21
>sudo adduser

Doesn't it work?

---

### Post by 1002285 on 2008-01-15
Is it possible to add an administrative user this way?
I was just making some changes to a system with LinuxMint, and somehow I am not able to log on anymore, although the changes were not about users at all. I formatted an old ntfs drive to ext3 with a LiveCD, but the system did not detect it as an ext3 partition. And, at the same time, none of the old users are able to log in. I managed to log in the "failsafe terminal" as the old user, but I created a new user using sudo adduser and this one is not able to delete and create users (that has worked with the same problem a couple of times - deleting the user and creating a new one with the same name).

*Edit*: the partition for /home had somehow got unmounted - lucky I thought of trying to umount the partition. So I mounted it again and am now logged in.

---

### Post by mali2297 on 2008-01-15
> **1002285 said:**
> Is it possible to add an administrative user this way?
I was just making some changes to a system with LinuxMint, and somehow I am not able to log on anymore, although the changes were not about users at all. I formatted an old ntfs drive to ext3 with a LiveCD, but the system did not detect it as an ext3 partition. And, at the same time, none of the old users are able to log in. I managed to log in the "failsafe terminal" as the old user, but I created a new user using sudo adduser and this one is not able to delete and create users (that has worked with the same problem a couple of times - deleting the user and creating a new one with the same name).

*Edit*: the partition for /home had somehow got unmounted - lucky I thought of trying to umount the partition. So I mounted it again and am now logged in.

To answer your question though, I think
```

sudo useradd -G admin yourusername

```
would have worked.

---

