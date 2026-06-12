---
title: "Crontab and Rsync"
date: 2009-03-13
forum: General Help
---

### Post by mjbauer95 on 2009-03-13
How would you get over the issue of Rsync always asking for a password?

My command in Crontab is this:
```
0 3 * * * rsync -r ~/Music 192.168.1.104:/Files/Music
```

But every time it asks for a password. Is there is any way to specify the password via Rsync?

---

### Post by dcstar on 2009-03-13
> **mjbauer95 said:**
> How would you get over the issue of Rsync always asking for a password?

My command in Crontab is this:
```
0 3 * * * rsync -r ~/Music 192.168.1.104:/Files/Music
```

But every time it asks for a password. Is there is any way to specify the password via Rsync?

Yes, and this show you how:

```
man rsync
```

---

### Post by mjbauer95 on 2009-03-14
Through --password-file?
If so when I run the command:
```
rsync --password-file=~/.rsync/192.168.1.104 -r ~/Music 192.168.1.104:/Files
```
It says:
```
The --password-file option may only be used when accessing an rsync daemon.
rsync error: syntax or usage error (code 1) at main.c(1257) [sender=3.0.3]
```

---

### Post by mjbauer95 on 2009-03-19
Any Help here?

---

### Post by mrsteveman1 on 2009-03-19
It appears to be telling you that you need to have rsyncd running

---

