---
title: "Bug #222643 seams to be alive!"
date: 2009-05-04
forum: General Help
---

### Post by larini on 2009-05-04
Hi, my 9.04 has the sames symptoms or worst.

A user X mount a CD.
Switch to user Y.
Switch to user X again and logout.
Login user Y. The CD remains mounted owned by user X..

Now I have a mounted media and only root can umount..

---

### Post by paradigm2 on 2009-05-05
> **larini said:**
> Hi, my 9.04 has the sames symptoms or worst.

A user X mount a CD.
Switch to user Y.
Switch to user X again and logout.
Login user Y. The CD remains mounted owned by user X..

Now I have a mounted media and only root can umount..

In /etc/fstab

```

cat /etc/fstab

```

Does "user" appear in the options for your CDrom?  

**Do not change itto the below.**  This is only what it might look like.  But there should be the option **user** in there.

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by larini on 2009-05-05
The mine is exactly the same.

---

### Post by nate_s on 2009-05-06
I believe you can change the 'user' to 'users' (note the s) to allow any user to be able to unmount a CD mounted by any other user.

---

### Post by larini on 2009-05-06
yeah. It looks ok now.
Thanks

---

