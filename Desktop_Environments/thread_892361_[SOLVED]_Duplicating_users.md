---
title: "[SOLVED] Duplicating users"
date: 2008-08-17
forum: Desktop Environments
---

### Post by moody_mark on 2008-08-17
Hi all,

I wanted a new user to have an identical desktop and settings to a current user. I created userA and set everything up just so. Then I created userB with their own home dir. I browsed a lot of the posts on here and it seems that you should just be able to copy the settings across from the home directory. So in fact this is what I done;

```
sudo cp -Ra userA/* userB/
sudo chown -R userB:users userB
```

However when i login as userB the settings etc (desktop background etc) and firefox bookmarks etc all remain unchanged

Am I missing something?

---

### Post by mali2297 on 2008-08-17
That command does not copy hidden files and directories, which are those that you want. 

Hidden files start with a dot, so use
```

sudo cp -R /home/userA/.??* /home/userB
sudo chown -R userB:users /home/userB

```

The expression '/home/userA/.??*' matches all files that starts with '.' and at least two more characters (to avoid recursively copying the present directory '.' and  the parent directory '..').

---

### Post by moody_mark on 2008-08-18
That worked like a charm! Thank you very much :)

---

