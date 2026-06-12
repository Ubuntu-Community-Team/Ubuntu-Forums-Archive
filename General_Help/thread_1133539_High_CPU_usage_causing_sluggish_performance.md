---
title: "High CPU usage causing sluggish performance"
date: 2009-04-23
forum: General Help
---

### Post by satish_j on 2009-04-23
Can anyone explain me why ubuntu uses 25% CPU on average as compared to 2% usage in WindowsXP.
I have this Ubuntu system which takes approx 1 second to navigate through Linux file system,while the same happens within a fraction of seconds on XP machine.
I think that this increase in CPU usage causes sluggish performance.
Is there any setting/Process needs to be done to speed it up.
I feel that,speedwise,XP leads Linux(pls correct me if iam wrong)
My idle Ubuntu system uses about 20% CPU(idle means not a single app is running),whereas the same idle position in XP will use at the most 2%(or may be 0%).
Any Help appreciated..

---

### Post by khelben1979 on 2009-04-23
> **satish_j said:**
> I feel that,speedwise,XP leads Linux(pls correct me if iam wrong)

This not a fair comparison of Linux since different distributions is configured differently.

From my own experience of using Ubuntu, I experienced it to be sluggish and slower than XP, however I strongly believe that you can change things in the system to speed it up.

In the /etc/init.d/ directory you can see all the scripts which is executed during start up and if you use the man command for these you'll see what they do (hopefully, if you understand it) and then you can begin to sort out scripts which you don't want to have running. This will make a speed boost. I think that there might be a graphical application which can handle this, but I'm not sure of it's name. Creating a directory inside that catalog structure and then move scripts over will turn them off.

There's graphical tools for system adminstration which hopefully can handle the thing which I've just mentioned.

Also using sudo top will show all the processes which you have active in the system and from there you can also analyze processes back and forth and using the man command to check them up.

[Wiki about the man command]("http://en.wikipedia.org/wiki/Man_page").

---

### Post by tom66 on 2009-04-23
Keep in mind if you are using gnome-system-monitor, it seems to eat about 10-15% CPU just doing the graphs, in my case.

---

### Post by krnekhelesh on 2009-04-23
You could run Sessions Manager from **System ->  Preferences -> Sessions** where you can choose the startup applications which are running and you can disable them.

Another thing which you can do is see the system Monitor from **System -> Administration -> System Monitor**, where you can check which processors are taking maximum CPU load. If it not a critical system process you can kill it.

---

### Post by satish_j on 2009-04-24
Thanks to all for your responses..I tested today with only 'Top' command and found that CPU usage was indeed 0.7%.It was system monitor(graphical) which showed me 20% of usage.
But,still navigation in Nautilus is slow as compared to xp..
whenever i hit back button in nautilus,usage peeks to 85% for some 1-2 seconds and then comes back to 0.So,during this 1-2 seconds,nautilus is just working and the mouse cursor becomes active.
Dont you peoples think that 1-2 seconds is too long for a file manager like Nautilus..
Also,for mounted drives,this time is around 2-3 seconds.

---

### Post by wfp on 2009-04-24
You also check to see what your processor is set at. Seems Ubuntu uses cpu scaling. I found out mine was set to on-demand which is set to default. I also noticed that when cpu was set to on demand firefox and other programs were all runing high around 40 to 60 percent in top. Now that I have set my cpu to 1.8ghz these processes rarely go over 10% and everything is much quicker. They say the kernel is smart enough to increase speed when needed but that has not been the case it least for me. I have htop open right now and nothing is using more that 2% of my cpu.

---

### Post by satish_j on 2009-04-24
Can you pls explain how to set the Processor from on-demand to 1.8GHZ??

---

### Post by satish_j on 2009-05-01
bump..:(

---

### Post by jakobtritten on 2009-05-01
bump

---

