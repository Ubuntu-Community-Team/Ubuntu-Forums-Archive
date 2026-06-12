---
title: "Question about OS Priority settings"
date: 2009-08-16
forum: Desktop Environments
---

### Post by peyre on 2009-08-16
Say, I'm curious about something.  In NT-based operating systems, by default (except on the server versions), the OS gives a higher priority to the highlighted application.  Do Ubuntu and its variants do the same kind of thing, or its equivalent?  Or does it matter what's highlighted?

Any info on how this sort of thing works (compared to, or opposed to, how it works in Windows) would be welcome to this old-timer NT/2000 MCSE. :-k

---

### Post by prshah on 2009-08-16
> **peyre said:**
> the OS gives a higher priority to the highlighted application.  

Process priority in Linux is controlled with the nice command. The "man"(ual) page for nice will give you detailed information. 

Summary: nice allows a process to have a "niceness" value from -19 to +20. The "nicer" the program is, the less likely it is to interrupt and "snatch" CPU time from other processes. The default nice level is "0" but each process takes it's priority level of it's parent.

Usually, most processes are spawned with an appropriate nice level for their function, so you should not need to manually adjust anything in particular.

You can manually "renice" a running process, or start a new process with a different "niceness" with the nice command.

You may also want to check out ionice.

---

### Post by peyre on 2009-08-16
Thanks!  I wondered.  It's good to get some more details about what nice is all about.  I had thought it was a funny term when I first learned about it.  So it seems there is no boost given to the active window; you have to manually alter the "niceness" of a process to give it a higher priority.  Is that right?

---

### Post by mcduck on 2009-08-17
> **peyre said:**
> Thanks!  I wondered.  It's good to get some more details about what nice is all about.  I had thought it was a funny term when I first learned about it.  So it seems there is no boost given to the active window; you have to manually alter the "niceness" of a process to give it a higher priority.  Is that right?

Yes.

Linux has a strong background as multi-user multitasking system. And when there are many users using the same system at the same time automatically giving higher priority to apps some user have selected could be problematic.

Actually normal user's can't give their apps higher priorities even with the nice command, hey are only able to lower the priority of the program (higher nice value).

To set nice values below 0 you need root permissions. And by the way, root can even set the nice values for *users*, so if you happen to be user on a large Unix/Linux system, better be friends with the admins or you might soon notice how everything you do seems rather slow.. ;)

Anyway, if you run a single-user system and want currently active application to have higher priority, the realtime kernel is what you are looking for. It's gives considerably higher priority to active program, and is commonly used with realtime audio & video tasks. Ubuntustudio includes realtime kernel by default but its also available in the repositories. (However this kind of approach is not very good for normal desktop use, browsers and text editors don't need such high priority and giving that to them will only make your desktop experience less smooth).

---

### Post by peyre on 2009-08-17
Wow, cool!  Thanks, that's good stuff to know.

I don't think I'll mess with the realtime kernel though.  That sounds potentially problematic, and I'm not experiencing performance issues anyway.

---

