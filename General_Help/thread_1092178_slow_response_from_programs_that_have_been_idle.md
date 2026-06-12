---
title: "slow response from programs that have been idle"
date: 2009-03-10
forum: General Help
---

### Post by dogooder on 2009-03-10
Here's my problem:

I have a program open but I haven't used it for a while (maybe twenty minutes or longer). I'm busy using some other program. Then I come back to the first program but it's unreponsive for a few seconds, sometimes going gray and giving the force quit dialog before finally responding.

Is there any way to fix this? It's really annoying. It seems to happen with any program (gedit, nautilus, banshee), although the other program I'm usually using is firefox. I'm not sure how long it has been going on--maybe forever. (I switched from Windows a couple months ago.) I'm on Ubuntu 8.10 and can give other details if they're requested.

---

### Post by prince_niceguy on 2009-03-10
How much ram your computer has? If the RAM is less then may be the program is being moved to swap and system is trying to read from swap so it becomes gray and remains unresponsive for some seconds.

---

### Post by dogooder on 2009-03-10
I have 1GB, with 2GB of swap. Firefox hogs a lot of memory, and java too. Right now according to system monitor: Memory 803.2 of 1001.0, Swap 707.2 of 1.9GB. (I think these values are higher than what they usually are.) How would I test if this was the problem?

---

### Post by Neo_The_User on 2009-03-10
> **dogooder said:**
> I have 1GB, with 2GB of swap. Firefox hogs a lot of memory, and java too. Right now according to system monitor: Memory 803.2 of 1001.0, Swap 707.2 of 1.9GB. (I think these values are higher than what they usually are.) How would I test if this was the problem?

Yeah thats terrible. I have no idea how you got it to use that much hahaha! a bit too high there eh? Just restart your computer. power off, power on.

---

### Post by prince_niceguy on 2009-03-10
do a sort by memory in system monitor and see who is taking the largest chunk of memory, might be some memory leak  or might be issue with some application.

also, type the command free in terminal to see how much is buffer/cached.

---

### Post by dogooder on 2009-03-10
Right now: firefox 261.1MB, java 114.0, banshee-1 74.2, and everything else is below 15MB. These are typical values.

```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       1025068    1013632      11436          0       6792     198648
-/+ buffers/cache:     808192     216876
Swap:      1951888     772852    1179036

```

---

### Post by prince_niceguy on 2009-03-10
are you seeing all process or only yours? try seeing all processes, should give more info.

---

### Post by dogooder on 2009-03-10
All processes only adds Xorg at 76.8MB.

So memory + swap totals about 1.5 GB, but the processes only total around 550MB. This is probably a silly question, but should those two numbers be the same? How do I figure out what's in the difference?

---

### Post by prince_niceguy on 2009-03-10
ya they should match... are there are lot of processes with same name or something? that could also be a problem like i had gvfsd-trash some 50 processes at a time which were taking lot of space. also do you use some desktop search like tracker or something?

have you tried disabling compiz and see if they still work slow or not?

---

### Post by dogooder on 2009-03-10
I've disabled compiz before (to watch movies fullscreen), but I don't remember if I had the problem then. But anyway, I think I might have found the problem:

In my firefox preferences, I had 5000MB set for the offline cache. In about.cache, for disk cache it said I had 655MB storage in use, but the specified directory had only 12MB. Was it storing stuff in swap? Anyway, I set the value back to 50MB (I don't know why I originally changed it--I've kept my profile over various computers), cleared it and restarted my computer. I've opened up all the same programs and now memory is 635.7MB, swap 7.2MB.

So this might have solved my problem if your hypothesis was right, prince_niceguy. I'll watch for it over the next day or so and report back. Thanks for the help.

---

### Post by dogooder on 2009-03-11
I haven't noticed the problem anymore, so I think I've solved it.

---

