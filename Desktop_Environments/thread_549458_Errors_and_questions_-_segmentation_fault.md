---
title: "Errors and questions - segmentation fault"
date: 2007-09-12
forum: Desktop Environments
---

### Post by Nightwalker107 on 2007-09-12
Hello,

My questions are about some problems that sometimes occurs on my computer. Here is the problem:

When I start the computer all applications runs fine, but after some time the machine is running I begin to receive the error Segmentation fault (core dumped). And the applications doesn't start after all.
When I restart my computer, everything come back to work normally.

First, It is not my first installation of the (K)ubuntu Feisty, so I guess another install will solve the problem... :(

As far as I know, this error is provoked by an invalid memory access (I don't know if may be other causes), like when a program try to access a SO memory area.
I tried to look at the log files of the system, but couldn't find anything about the error. (Maybe I'm looking at the wrong place).

Another thing, this issue seems to be restricted by the user that is receiving it. I can execute the firefox as root (using sudo firefox), but I can't with my user.

So it seems something related with the session.

Another thing I realized was that it was occurring with the GNOME based applications, like GAIM, GIMP...

I made the memory test for 10 hours, the result was 32 pass and 0 fails... So I believe it is not a memory issue.

This problem is boring me, because one of the most talked and betest attributes from linux is the stability, and it means that I will not need to be restarting my computer always, like I'm having to do.

So, I tried to figure out why it is happening but I couldn't :(

Anyone have any clue of why this is going on, and how can I solve, or minimize the problem?

Any info about the PC and configurations you think is relevant, please just let me know.

Thanks for the help in advance.

---

### Post by Nightwalker107 on 2007-09-13
Everyone is so lost like me in this case? :confused:

Well, I was thinking, that maybe, it may be caused by some component of the gnome that are shared by the applications.
I mean, a shared code that stays in memory, and all GNOME applications uses it to build it windows. And maybe, if it is true, if I could restart this process (component) used, the problem is solved.

Anyone knows something regarding to this, or knows if this theory have some sense?

Thanks

---

### Post by Happy_Man on 2007-09-13
No, if you restarted your computer, it will reload everything anyway. My advice, would be to set up a separate /home partition (if you haven't already)(use the link in my sig) and then reinstall.

---

### Post by sloggerkhan on 2007-09-13
If you think it's a gnome dependancy, maybe try installing gnome desktop package?

---

### Post by Happy_Man on 2007-09-13
I hadn't thought of that. Why don't you run ```
sudo apt-get install ubuntu-desktop
``` and see what happens?

---

### Post by Nightwalker107 on 2007-09-13
Hi,

The ubuntu-desktop is already installed, and the /home is in other partition than the system.
Before post here, I already reinstaled the SO, applyed all updates. I have both, ubuntu-desktop and kubuntu-desktop installed.

Any clues?

---

