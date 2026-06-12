---
title: "libwnck-1.so.18"
date: 2007-10-18
forum: Desktop Environments
---

### Post by r4ndom on 2007-10-18
i was trying to launch emerald themer with my newly updated gutsy gibbon install when it failed to load. Having ran it via terminal i realised i was missing a dependancy called "libwnck-1.so.18." This however appears to be deprecated or something as it is not in the database. Although it has been replaced with libwnck22 my install appears not be able to use this. Perhaps it is an error with the updater? Any thoughts on this? I'll probably get back tommorow so if you have any ideas.

thanks in advance :KS

---

### Post by rmx.dave on 2007-10-19
Also having this problem...

---

### Post by hanzomon4 on 2007-10-22
```
sudo ln -sf /usr/lib/libwnck-1.so /usr/lib/libwnck-1.so.18


```

---

### Post by hanzomon4 on 2007-10-22
Oops had a slight typo, fixed now

---

### Post by r4ndom on 2007-10-24
> **hanzomon4 said:**
> Oops had a slight typo, fixed now

oh thank you very much. :KS perhaps add sudo to the beggining of the command as well because those directories are restricted(will help newbies). I now appear to have compiz working!

---

### Post by hanzomon4 on 2007-10-25
> **r4ndom said:**
> oh thank you very much. :KS perhaps add sudo to the beggining of the command as well because those directories are restricted(will help newbies). I now appear to have compiz working!

;)

---

### Post by denham2010 on 2007-10-26
Hi,

Just want to add, when I upgraded from Feisty to Gutsy, this affected my install of AWN. Same fix worked - ie creating a symlink and naming it as AWN would expect to find it.

---

### Post by dunomous on 2008-02-23
> **denham2010 said:**
> Hi,

Just want to add, when I upgraded from Feisty to Gutsy, this affected my install of AWN. Same fix worked - ie creating a symlink and naming it as AWN would expect to find it.

So, I may have messed up here, then. I ran the above command and now get this error:

```
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_vfs_init
```

What shall I do?

---

