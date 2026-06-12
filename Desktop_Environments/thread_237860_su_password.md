---
title: "su password"
date: 2006-08-16
forum: Desktop Environments
---

### Post by DagonX on 2006-08-16
I tried to install Sun Java 5.08 in a directory named Java, for a lack of a better name. The file manager wanted the su password. It wouldn't take the local login password or either of the two login names I used when installing Ubunto. So what is the su password? Or how do I create a directory under root? By the way mkdir had the same problem.

---

### Post by taurus on 2006-08-16
Try putting sudo in front of the command.  Then use the same password that you use to log in to your regular account...

```

sudo <command>

```

---

### Post by Jagot on 2006-08-16
If you type su, the password it will ask for is that of the first user.  To make a directory under, other than logging in as root:

```
sudo mkdir /wherever/you/want
```

---

