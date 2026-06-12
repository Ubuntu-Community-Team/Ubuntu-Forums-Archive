---
title: "arbitrary command"
date: 2009-06-09
forum: General Help
---

### Post by dhruwajita on 2009-06-09
hi all,
 
i want to know , can we execute an arbitrary command on a remote computer and what is the exact process for doing so....how can we have shell????????
 
 
 
plz answer!!!!!!!!!!!!!!

---

### Post by justleen on 2009-06-09
You would need ssh on the remote machine, and an account.
On the remote machine : apt-get install openssh-server

once that is done, you could send any command over ssh (the part between "" is the command that is remotely executed)
```
ssh user@remote "ls -ls /etc/" 
```

---

### Post by dhruwajita on 2009-06-10
thanks a lot.....but can we do these things in windows also..............if yes..how? plz explain.
 
thanks in advance..................

---

