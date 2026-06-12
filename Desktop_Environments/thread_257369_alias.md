---
title: "alias?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by stereotaxon on 2006-09-14
Hi, I'm using Dapper 6.06 and the alias command seems to be broken...

user@home:~$ alias ls 'ls -tral'
bash: alias: ls: not found
bash: alias: ls -tral: not found

Also, I'm trying to store aliases in .bash_aliases (and have also tried .bashrc) and neither method seems to work.  .bash_aliases is ignored, or so it seems, and I get similar errors to the one listed above in .bashrc.

Any ideas?  Thanks for your help!

---

### Post by thec0der on 2006-09-14
alias ls='ls -tral' is correct syntax

---

### Post by stereotaxon on 2006-09-14
Yes...but I've tried it with and without using the '=' all to the same result type as listed above...](*,)

---

### Post by cwaldbieser on 2006-09-15
> **stereotaxon said:**
> Yes...but I've tried it with and without using the '=' all to the same result type as listed above...](*,)

Make sure you are not using spaces around the =.
What happens if you do
```

$ type alias
$ type ls

```

---

