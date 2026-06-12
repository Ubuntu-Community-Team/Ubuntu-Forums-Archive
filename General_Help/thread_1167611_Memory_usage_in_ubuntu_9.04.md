---
title: "Memory usage in ubuntu 9.04"
date: 2009-05-23
forum: General Help
---

### Post by walterp98@gmail.com on 2009-05-23
Hello ....

I've been using ubuntu for 2-3 years now (6.06, 8.10, 9.04), and have always wondered about its memory usage.

I started out with 512 mb ram and noticed that the output of 'top' indicated that all memory was being used.  I recently upgraded to 1 Gb and still, all memory is being used.  I'm about to go to 2 Gb and wonder if it will all be marked as used.

Is this an FAQ item somewhere? Is this normal behavior?

Curious ...

Walter

---

### Post by DeMus on 2009-05-23
> **walterp98@gmail.com said:**
> Hello ....

I've been using ubuntu for 2-3 years now (6.06, 8.10, 9.04), and have always wondered about its memory usage.

I started out with 512 mb ram and noticed that the output of 'top' indicated that all memory was being used.  I recently upgraded to 1 Gb and still, all memory is being used.  I'm about to go to 2 Gb and wonder if it will all be marked as used.

Is this an FAQ item somewhere? Is this normal behavior?

Curious ...

Walter

It's a fact that Linux uses the installed memory because it is there. Why else did you buy it?
I have 4GB and use 2.8 at the moment. Don't worry about it, just use it. It's way faster than a swap file on disk.

---

### Post by binbash on 2009-05-23
Quite normal.You should know linux ram managament if you are using linux for 2-3 years.Buffers, cached and used ram is different.

Mem:          2005       1439        566          0         81        867
-/+ buffers/cache:        490       1515

As you can see , it seems i have 566 ram free but indeed i am using 490 and rest of them are usable ;)

---

### Post by mcduck on 2009-05-23
Yes, all the RAM will be used. The part that programs are not using is used as temporary cache for recently accessed data. If the programs then need more memory some cached data is dropped so cache still counts as free memory (in the sense most people coming from Windows would understand free memory).

Run "free -m" in a terminal, and check the "-/+ buffers/cache"-line to see how much memory your programs are really using and how much is still available for them if they need it.

---

### Post by walterp98@gmail.com on 2009-05-23
Thanks for all the responses.  I was shocked how much smoother even xubuntu got when I went from 512 mb to 1 Gb.  

Should I expect a similar jump when I upgrade to 2 Gb this weekend?

Walter

---

### Post by DeMus on 2009-05-23
> **walterp98@gmail.com said:**
> Thanks for all the responses.  I was shocked how much smoother even xubuntu got when I went from 512 mb to 1 Gb.  

Should I expect a similar jump when I upgrade to 2 Gb this weekend?

Walter

No, I wouldn't expect that. When you run many applications and you should run out of memory now, then there will be an increase in speed, but only then.
When you don't use the maximum yet with the things you normally do then it will be about the same. It's just that you can do more at the same time without slowing down.

---

### Post by mcduck on 2009-05-23
> **walterp98@gmail.com said:**
> Thanks for all the responses.  I was shocked how much smoother even xubuntu got when I went from 512 mb to 1 Gb.  

Should I expect a similar jump when I upgrade to 2 Gb this weekend?

Walter

Nothing big, I've found 1GB to be the "sweet spot" for Ubuntu when things start working nice. After that the difference is quite small (mainly coming from being able to keep more data cached) and you won't notice any significant difference unless doing something that really needs that much memory.

---

