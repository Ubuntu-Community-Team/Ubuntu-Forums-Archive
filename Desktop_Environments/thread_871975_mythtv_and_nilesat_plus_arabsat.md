---
title: "mythtv and nilesat plus arabsat"
date: 2008-07-27
forum: Desktop Environments
---

### Post by koba101 on 2008-07-27
Hi,

I'm trying to install mythTv on hardy.  My major problem now is scanning channels.  I've tried to put the frequencies that I know work, yet I don't see any channels.

My problem is that I can see nilesat and arabsat.  

Can anyone help me on this? I'm just focusing on the frontend for now (just watching TV)

Thanks,

---

### Post by koba101 on 2008-07-28
hi..can anyone reply to this?

---

### Post by akyd on 2008-07-30
I also have this problem.
I don't know how to add nilesat and arabsat to mythtv.
Can anyone help us, please??

---

### Post by karatchov on 2009-09-09
Hello,
I was looking for an answer of this same question.

The solutions is to use manual scan: open terminal and type:

```
scan /usr/share/dvb/dvb-s/Nilesat101+102-7.0W > channels.conf
```

It seems there is no file for arabsat, so goodluck with it :D

---

