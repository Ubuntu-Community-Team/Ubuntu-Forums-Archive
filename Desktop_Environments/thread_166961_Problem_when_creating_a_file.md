---
title: "Problem when creating a file"
date: 2006-04-27
forum: Desktop Environments
---

### Post by etiennemula on 2006-04-27
Hi all, i am trying to do a simple backup utility. I have opened a new txt file and typed the copy source destination files which i want to take a backup of them.

Now my problem is that i thnk that when i am going to run this file through cron it will  ask me for the root password. I dont want this because it is going to be automated. What should i write in the txt file where i issued the copy commands so that the cron identifies the password.

Any help will be appreciated.
Thanks

---

### Post by cgjones on 2006-04-27
Just add the script to root's crontab.
```

sudo crontab -u root -e

```

---

### Post by Ramses de Norre on 2006-04-27
Add it to /etc/sudoers with a NOWPASSWD statement. Add line ```
username    ALL=NOPASSWD /path/to/file
```

EDIT: use above method ;)

---

