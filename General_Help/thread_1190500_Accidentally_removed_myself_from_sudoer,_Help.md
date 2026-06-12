---
title: "Accidentally removed myself from sudoer, Help"
date: 2009-06-17
forum: General Help
---

### Post by chuugokujin on 2009-06-17
Ubuntu 9.04
I screwed up by using usermod -G to put myself into a group, now I lost all my groups. I am no longer a sudoer.
Please help me retrieve my groups, or at least get myself into sudoer list.
I tried log in as root but neither my password nor empty password allows me to get in.

Help, I appreciate it.

---

### Post by redilyn on 2009-06-17
Restart your computer and select recovery mode then root prompt.

entry the following command changing name_of_user to your username

```

sudo adduser name_of_user admin

```

---

### Post by ptn107 on 2009-06-17
```
usermod -a -G admin <user>
```
Replace <user> with your username.

---

### Post by chuugokujin on 2009-06-17
I used the recovery way and it is solved!
Grazie!

---

