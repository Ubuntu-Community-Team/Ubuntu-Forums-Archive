---
title: "Monitoring Server"
date: 2009-09-25
forum: Desktop Environments
---

### Post by randomj on 2009-09-25
Hey Guys,

I'm an IT Admin at our company and I'd really like to use Ubuntu for our monitoring PC. What would be really nice is if we could use the multiple desktops to rotate around different log screens. 

If we could see screen 1 for 30 secs, then screen 2 for 30 secs, then screen 3 and so and so forth until we see screen 1 again. Ideally it'd be all completely automated and all we'd see is just a big screen showing different screen every 30 secs.

What do you guys think? Is it possible?

Thanks in advance!

James

---

### Post by Giblet5 on 2009-09-25
Take a look at the third post in [this thread]("http://ubuntuforums.org/showthread.php?t=1274532") for details on creating the "compiz-rotate" script.

With that script, this will do what you want:
```
while true
do
  sleep 30
  ./compiz-rotate right
done
```

---

### Post by mister_p_1998 on 2009-09-25
> **randomj said:**
> Hey Guys,

I'm an IT Admin at our company and I'd really like to use Ubuntu for our monitoring PC. What would be really nice is if we could use the multiple desktops to rotate around different log screens. 

If we could see screen 1 for 30 secs, then screen 2 for 30 secs, then screen 3 and so and so forth until we see screen 1 again. Ideally it'd be all completely automated and all we'd see is just a big screen showing different screen every 30 secs.

What do you guys think? Is it possible?

Thanks in advance!

James

We used to use a program called RM Tutor on our schools RM Connect Server2000/XP network. Did exactly what you want.. great fun on a Friday afternoon after a couple of pints in the pub, watching the kids trying to get on dodgy sites, then taking over their stations remotely and logging them off!
Im sure theres an open source equivalent.
Steve

---

