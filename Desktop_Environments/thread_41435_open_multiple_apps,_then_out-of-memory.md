---
title: "open multiple apps, then out-of-memory"
date: 2005-06-13
forum: Desktop Environments
---

### Post by oasiscity on 2005-06-13
Hi,

I open firefox, thunderbird, rythembox, and at last open real-player and trying to start playing a movie, then...
my HD began working endlessly, my desktop is almost frozen, with only pointer still being able to move, slowly..

after my HD struggling for a while, one of application was killed by the system,
then my desktop comes back to life.

I come to this recently. I didn't remember I have this problem in the first days after I installed ubuntu. 

this really annoys me. I serched with "memory usage" in this forum, and find that there have been similar   threads already. One of them mentioned that the guy had tried the "hibernate". I tried, too... I don't know if this is the problem.

Hopefully there are some developers in this forum, who can solve this issue.


------
I have 256 RAM. Athlon XP 1600+

---

### Post by shakin on 2005-06-13
[QUOTE=oasiscity]Hi,

I open firefox, thunderbird, rythembox, and at last open real-player and trying to start playing a movie, then...
my HD began working endlessly, my desktop is almost frozen, with only pointer still being able to move, slowly..

after my HD struggling for a while, one of application was killed by the system,
then my desktop comes back to life.

I come to this recently. I didn't remember I have this problem in the first days after I installed ubuntu. 

this really annoys me. I serched with "memory usage" in this forum, and find that there have been similar   threads already. One of them mentioned that the guy had tried the "hibernate". I tried, too... I don't know if this is the problem.

Hopefully there are some developers in this forum, who can solve this issue.


------
I have 256 RAM. Athlon XP 1600+[/QUOTE]

From a terminal run 'free' to see how much RAM is in use and how much swap is being used. Run the System Monitor and sort by vm size to see which processes are taking up a lot of RAM. Hopefully you can catch an app misbehaving, then you'll know what to avoid or which app to upgrade to hopefully solve the problem.

Of course, with 256MB RAM you might want to look into a light-weight window manager such as XFCE or Fluxbox. Running either of those will help tremendously.

---

### Post by nocturn on 2005-06-14
When this occurs, can you drop to a console (CTRL-ALT-F1), log in and run top?
What does it show?

---

### Post by Andrei on 2005-06-14
Hmm...if your rhythmbox is adding music to your library...chances are that is causing the problem...

Also...with 256 mb of ram u are cutting it a bit thin...my guess is that realplayer kills it all...

---

### Post by oasiscity on 2005-06-14
[QUOTE=nocturn]When this occurs, can you drop to a console (CTRL-ALT-F1), log in and run top?
What does it show?[/QUOTE]

In this state, it is nearly impossible to switch to the console. the system seems to be a frozen state, with the harddisk working all the time.

The following is a snapshot of TOP command output, ordered by mem usage.
I opened amarok, firefox, thunderbird,
you can see, my RAM is already with heavy load.
the system still works well, a bit slow. but if I open another app, like real, 
I bet the system will be frozen again.

------------------------------------------------------------------------------
top - 21:54:21 up 20 min,  3 users,  load average: 0.70, 1.13, 1.01
Tasks:  81 total,   1 running,  79 sleeping,   0 stopped,   1 zombie
Cpu(s): 75.0% us, 25.0% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    256664k total,   252128k used,     4536k free,     1752k buffers
Swap:        0k total,        0k used,        0k free,    43668k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7645 zwf       15   0  142m  35m 5516 S 58.3 14.0   1:02.60 amarokapp
 7541 zwf       15   0  117m  31m 8604 S  0.0  12.6   1:21.78 firefox-bin
 5941 root      15   0  102m  29m 3412 S  0.0 11.7   0:58.70 Xorg
 7853 zwf       15   0  105m  25m  15m S  0.0 10.4   0:06.34 mozilla-thunder
 7864 zwf       15   0 44920  13m 9620 S 58.3  5.3   0:03.08 gnome-terminal
 7429 zwf       15   0 51772  12m 5276 S  0.0  5.1   0:02.94 nautilus
 7463 zwf       15   0 51096  10m 4776 S  0.0  4.0   0:02.02 mono
 7431 zwf       15   0 41192 9868 5244 S  0.0  3.8   0:02.62 gnome-panel
 7527 zwf       15   0 17288 8204  952 S  0.0  3.2   0:00.09 scim-launcher
 7378 zwf       16   0 12040 7760 1056 S  0.0  3.0   0:01.32 gconfd-2
 7450 zwf       15   0 30316 7644 4508 S  0.0  3.0   0:02.07 wnck-applet
 7427 zwf       15   0 24860 6632 4492 S  0.0  2.6   0:02.26 metacity
 7476 zwf       15   0 21056 6196 3192 S  0.0  2.4   0:00.94 mixer_applet2
 7474 zwf       15   0 29848 5988 3460 S  0.0  2.3   0:00.51 clock-applet
 7443 zwf       15   0 33468 5932 3348 S  0.0  2.3   0:00.68 update-notifier
 7320 zwf       15   0 29772 5560 2468 S  0.0  2.2   0:00.71 gnome-session
 7536 zwf       15   0 33024 5124 3144 S  0.0  2.0   0:00.87 scim-panel-gtk

---

