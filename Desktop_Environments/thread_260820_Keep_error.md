---
title: "Keep error"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Branta on 2006-09-19
Ubuntu 6.15  - Gnome - I am the only user - have admin priv.

I am backing up to a backup directory I created in a flash drive.

When running _Keep_ in _both backup and restore_ I get this error at the end  of each run.

```

An error occured restoring /media/TRAVELDRIVE/backup backup:
ListError .gnupg [Errno 13] _Permission denied_: '/home/bob/.gnupg'
```

What should I do?

-- Bob --

---

### Post by lagagnon on 2006-09-19
Well that means your ~/.gnupg directory does not have permissions set to allow those programs to read it. Check its permissions with "ls -al .gn*"

If you need to brush up on Linux permissions then read this:
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

The reason being is that ~/.gnupg may store your private and public keys if you have created them and you surely don't want anyone but yourself to see the private one. You should probably exclude that directory from backup - I would.

---

