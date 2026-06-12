---
title: "What is eating up all my swap memory?"
date: 2009-02-27
forum: General Help
---

### Post by Giant Speck on 2009-02-27
Before I reinstalled Ubuntu 8.10 last time, I never saw very much usage of swap memory.

However, ever since I have reinstalled, my computer has been using an enormous amount of swap memory with barely anything running.

I don't have anything running in the screenshots below besides Compiz and Cairo-Dock, and neither of those two use much memory.

I've already tried reducing my system's swappiness from the default 60, but it hasn't done a thing.  How do I find out what is using up this memory and kill it?

---

### Post by Alterax on 2009-02-27
> **Giant Speck said:**
> Before I reinstalled Ubuntu 8.10 last time, I never saw very much usage of swap memory.

However, ever since I have reinstalled, my computer has been using an enormous amount of swap memory with barely anything running.

I don't have anything running in the screenshots below besides Compiz and Cairo-Dock, and neither of those two use much memory.

I've already tried reducing my system's swappiness from the default 60, but it hasn't done a thing.  How do I find out what is using up this memory and kill it?

Go to the terminal and type the following command:  *You do _not_ need root access to do this.*
```

free -m > free.txt
```

What this does:  the **free** command gives general statistics on memory usage. Using the -m tag puts the results into megabytes.  The > pipes the results into the file "free.txt".

Attaching that file will just let me know how much memory we're starting off with.

Next run the **top** command.  Once top is running, press the **m** key.  Top is used to determine the resources used by the processes on the system.  Pressing the m key lets you know the memory used by each.  Jot down the names of the top 2 or 3 on the list, along with their figures on the VIRT, RES, and %MEM columns.  This listing WILL change quite a bit, but you can just press **q** to quit and take the readings from the leftover bits of the list.

Once you get that, attach the text file from above and the results from the top command, and I can see what we can do here.

---

### Post by Alterax on 2009-02-27
Actually ignore the bit about the "top" command.

You're running Compiz and emerald; what type of graphics card are you running with?  And are you running the proprietary or the open-source drivers?  Some of the non-proprietary drivers have issues accessing the full advantages of the card.  If that is the case, quite a bit of the system resources may be taken up handling the desktop effects, forcing processes that can handle it to take up swap space.

In a nutshell, drop the desktop effects and reboot, then let us know what happens.

---

### Post by ramjet_1953 on 2009-02-28
How much RAM dos your system have?

Regards,
Roger

---

### Post by Giant Speck on 2009-02-28
This is going to sound crazy, but before I logged off and logged back on, I went into the Sessions dialog and added the "metacity --replace" command and I unchecked the box that automatically starts Cairo-dock.  Then I logged off.

When I logged back in, Metacity started instead of Compiz, as I wanted, and I got the following from the terminal:

```
jesse@jesse:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999        533        466          0         13        213
-/+ buffers/cache:        306        693
Swap:          956         14        942

```Then I went back into the Sessions dialog and edited it so that Compiz and Cairo-Dock would start automatically. I logged out and back in, and then ran "free -m" in the terminal again.  This is what I got:

```
jesse@jesse:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999        598        401          0         13        213
-/+ buffers/cache:        371        628
Swap:          956         14        942

```

I'm guessing that I've been having Compiz automatically start for so long that it was starting to gunk up my machine and force Ubuntu to use swap.  Does this make sense?

Anyway, it seems my problem is fixed...

---

### Post by Yellow Pasque on 2009-02-28
> I'm guessing that I've been having Compiz automatically start for so long that it was starting to gunk up my machine and force Ubuntu to use swap. Does this make sense?
No. I don't think you ever had a problem to begin with, but you just need to read up on how virtual memory works.

---

