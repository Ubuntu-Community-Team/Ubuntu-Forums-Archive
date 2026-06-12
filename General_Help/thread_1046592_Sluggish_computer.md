---
title: "Sluggish computer"
date: 2009-01-21
forum: General Help
---

### Post by Liliitha on 2009-01-21
I have had Ubuntu for abouta month now and as time progresses the computer gets more and more sluggish.  I am unsure why this is happening.  Things that go slow are things like the typing, the words while when I try to delete them with backspace.  The computer programs are very choppy in motion and things take a while to load up.  This was not the case when I had first installed the OS though.  Any ideas on what is going on?  I have 512 memory is that enough?

---

### Post by SteveDee on 2009-01-22
> **Liliitha said:**
> I have had Ubuntu for abouta month now and as time progresses the computer gets more and more sluggish.  I am unsure why this is happening.  Things that go slow are things like the typing, the words while when I try to delete them with backspace.  The computer programs are very choppy in motion and things take a while to load up.  This was not the case when I had first installed the OS though.  Any ideas on what is going on?  I have 512 memory is that enough?

I suggest you run System Monitor ( System > Administration > System Monitor) and take a look at "Processes".

You should be able to see from this list what processes are running and how much %cpu they are using.

I think its a good idea to add System Monitor to your panel so you see a mini graph of %cpu. I sometimes get problems with my printer after a print, where the process keeps running and consuming 50% of my cpu time. The graph helps me spot the problem and fix it.

---

### Post by Liliitha on 2009-01-27
It says average CPU usage is 95% and memory usage is 70% while Swap is 20%
I only have 4 Firefox windows open though... Would more memory fix this problem?

---

### Post by mb_webguy on 2009-01-27
Look at the processes list to see what processes are using the most system resources.  If you keep 4 Firefox windows open, that could be the problem.

And yes, increasing your memory is usually a good way to speed up your computer.  Too many people focus on getting a fast processor and neglect memory.  Even the current low-end processors have more than enough speed for most day-to-day computing requirements, but it doesn't matter how fast your processor is if you don't have adequate memory for the applications you're running.

---

### Post by SteveDee on 2009-01-27
> **Liliitha said:**
> It says average CPU usage is 95% and memory usage is 70% while Swap is 20%
I only have 4 Firefox windows open though... Would more memory fix this problem?

I doubt if memory is your problem (..and don't go spending your hard earned money just yet!;)).

The first thing I would do is look at the processes list in System Monitor.

From the View menu select "My Processes" and deselect "Dependencies". Now click on the %CPU column so that the arrow is pointing upwards.

You should see the most hungry processes at the top of the list, and the values changing every few seconds. (in the attached graphic I also have Firefox running with 4 tabs open). Hopefully this will show where 95% of cpu time is going, and also where 70% memory is being used.

You say your computer is sluggish, so also try running System Monitor while displaying "Resources", so you can see the CPU history, Memory & swap graphs. Now load up an application that demonstrates the sluggishness problem (maybe Open Office word processor on a 2nd desktop). 

Now take a look back at the System Monitor graphs. Are there memory problems?

---

### Post by Liliitha on 2009-01-28
The CPU percent usage does not add up right.  It will go up to 100% usage while it says firefox is sleeping and has 4% usage and system moniter only has 30% usage.

---

### Post by Liliitha on 2009-01-28
I have also found out that the internet is extremely slow now.  I looked at the network graph and while it is loading it still frequently goes to 0kbps for 10-30 seconds...  plz help :(

---

### Post by SteveDee on 2009-01-29
> **Liliitha said:**
> The CPU percent usage does not add up right.  It will go up to 100% usage while it says firefox is sleeping and has 4% usage and system moniter only has 30% usage.

OK, so it looks like you don't have a problem with Firefox. Now go into System Monitor > Processes. Select the "View" menu and select "Active Processes".

Hopefully the other processes that are running (which account for the rest of the %cpu usage) will appear. If you have enabled the "user" column (via Edit > Preferences > Processes) you can also identify the account these are run under (probably "root").

---

