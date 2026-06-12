---
title: "help me recover, I killed pam authentication I can't log at all"
date: 2006-07-31
forum: Desktop Environments
---

### Post by mirak63 on 2006-07-31
ok, I did a bad thing, I wanted to install a new libpam-mount version, so I grabbed tar ball and did make install with checkinstall, and stopped it in the middle of the running, and now I can't log exept with root.

when I try to log as a user, it says me unable to cd to /home/myuser.
I don't know what to do, I tried to reinstall but it dosn't fix the problem, something else might have happen.

#-o

---

### Post by mirak63 on 2006-07-31
just for the record :mrgreen: 

```
:/# ls -ld .
drwx------ 24 root root 736 2006-07-31 21:59 .

```

I don't know how this happened, but / was rwx------  ](*,)

\\:D/

---

### Post by TripleE on 2006-07-31
> **mirak63 said:**
> just for the record :mrgreen: 

```
:/# ls -ld .
drwx------ 24 root root 736 2006-07-31 21:59 .

``` 
I don't know how this happened, but / was rwx------  ](*,)

\\:D/

If the permissions are messed up on the entire dir, you may have to:
```
sudo chown -R myuser.myuser /home/myuser

```

---

