---
title: "Ubuntu freezes frequently, RAM not full"
date: 2020-01-25
forum: Desktop Environments
---

### Post by liubomirwm on 2020-01-25
Hi!

I have a very strange issue that i cannot understand why is happening. I am an Ubuntu user since maybe a year or so, and i really like the OS. However, since some time my Ubuntu freezes frequently. My PC is an Acer Aspire with 8gb of RAM and an Intel Core i5 8250u. I've tried keeping an htop open and quickly switching to it when the freeze happens, and i didn't saw the RAM was full. One time i saw that the swap was full, but my RAM had around 1.8 - 2.0 GB full RAM. I tried changing the swappiness to 10 from 60, but it continued to freeze. I can't seem to find a rule about when this happens. Maybe switching tabs and windows might be the cause, but sometimes it just gets slow to respond. Two or three times it completely froze so i used REISUB. I've never had issues with RAM on Windows 10 when i was using it. (Not saying to make someone angry, just a fact). Please help me trace down the issue, i am not exactly good at Ubuntu internals. I believe the PC wasn't freezing when i was on 19.04, it was fast.

---

### Post by TheFu on 2020-01-25
Check the system log files.  Could be that some hardware is failing.

I have that same CPU, similar RAM.  Had a few extreme slow-downs, never locked up. Ended up having to ssh into the machine from another to see what was going on.  Firefox had ballooned to using 9G of RAM.  Turned out that the installation didn't create enough swap.  I made it so there was 4.1GB of swap and it isn't happened again.  Now the system gets slow in a way I can "feel" as RAM becomes over-committed. This let's me close the hog programs before it is so slow that the system appears to lock up.  

But first, check the system logs for hardware issues.  I grep for errors and warnings in all those files.  **journalctl** can search the logs or just use grep.

---

