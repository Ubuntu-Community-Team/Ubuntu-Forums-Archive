---
title: "Deleting a user directory."
date: 2009-01-14
forum: General Help
---

### Post by Plan B on 2009-01-14
Hi.

I was experimenting with creating different user accounts.  Finished and removed the newly created users, but the user directory still remains in the home folder and I don't have permission to remove it.  The owner of the directory is listed as 1001.

drwxr-xr-x 22 1001 user2 4096 2008-12-15 21:42 user2

How do I trash it?

---

### Post by Titan8990 on 2009-01-14
IF the users name was user2:

sudo rm -rf /home/user2


This will delete the user's home directory and all subdirectories.

---

### Post by Plan B on 2009-01-14
That worked, thanks.


Question 2:
Where's the give thanks button gone?

---

### Post by sisco311 on 2009-01-14
when you create a new user(user2) the system creates a new group (with the same name: user2).

you may also want to remove this group:
```
sudo groupdel user2
```

you also can run your file manager, as root, to delete the directory:
```
gksu nautilus
```

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by Titan8990 on 2009-01-14
> 
Question 2:
Where's the give thanks button gone?

It has not been there since the forum problems yesterday.

---

### Post by Slim Odds on 2009-01-14
> **Plan B said:**
> Question 2:
Where's the give thanks button gone?

I was wondering the same thing......

I also wonder why the forums have been down so much lately...

---

### Post by sisco311 on 2009-01-14
> **Plan B said:**
> That worked, thanks.


Question 2:
Where's the give thanks button gone?

it has been turned off (temporarily) along with the "mark solved" feature:

[http://ubuntuforums.org/showthread.php?t=1038839]("http://ubuntuforums.org/showthread.php?t=1038839")

---

### Post by Plan B on 2009-01-14
Okay.

That also answers my third question: Where's the thread solved option?

:D

---

### Post by sisco311 on 2009-01-14
d'oh!!

i've edit my post above.
it's disabled as well.

---

