---
title: "problem with xubuntu on ps3"
date: 2009-05-23
forum: General Help
---

### Post by Moonsocket on 2009-05-23
i just installed xubuntu on my ps3 when ever im trying to change some thing it says i dont have the authorization to do so when i try to change some thing in terminal it says im not a sudoer ive tried going to users and group but it wont let me what do i do

---

### Post by taurus on 2009-05-23
Are you the original user that you created during the installing process?

What's the output of this command from a terminal?

```
id
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Moonsocket on 2009-05-23
> **taurus said:**
> Are you the original user that you created during the installing process?

What's the output of this command from a terminal?

```
id
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
ya im the original user and it says
uid=1000 gid=1000 groups=1000

---

### Post by taurus on 2009-05-23
> **Moonsocket said:**
> ya im the original user and it says
uid=1000 gid=1000 groups=1000

Whatever you did or modified, you've managed to remove yourself from group admin.  Therefore, sudo/gksudo won't work for you again.  You need to boot into recovery mode from GRUB menu, get into root shell, and add yourself back to group admin.

---

### Post by Moonsocket on 2009-05-23
> **taurus said:**
> Whatever you did or modified, you've managed to remove yourself from group admin.  Therefore, sudo/gksudo won't work for you again.  You need to boot into recovery mode from GRUB menu, get into root shell, and add yourself back to group admin.
dont think i did any thing cause the first thing i did after i installed xubuntu was trying to change the login screen but it wouldnt let me so im reinstalling it now just in case

---

