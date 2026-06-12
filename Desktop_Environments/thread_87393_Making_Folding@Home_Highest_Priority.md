---
title: "Making Folding@Home Highest Priority"
date: 2005-11-08
forum: Desktop Environments
---

### Post by el barto on 2005-11-08
Okay, I'm a linux newbie.  I have installed Breezy Badger and it's working okay with most stuff.  However, I have downloaded FOlding@home and can get it to run via the terminal, but it's not using anywhere near 100% CPU usage.  I have set the priority to high.  Is there any way to make it use all spare CPU cycles like it does in Windows XP?  I'm not so sure I can do it from GNOME if I run it from a terminal.  I read through the FAQ on the folding at home website, is there  a command I need to put in before/after the filename to make it run at highest priority?  I checked the usage with the "system manager" or whatever it's called and it's only using like 1-2% of the CPU power.  

Help would be greatly appreciated.

---

### Post by heimo on 2005-11-08
[quote=el barto]Okay, I'm a linux newbie.  I have installed Breezy Badger and it's working okay with most stuff.  However, I have downloaded FOlding@home and can get it to run via the terminal, but it's not using anywhere near 100% CPU usage.  I have set the priority to high.  Is there any way to make it use all spare CPU cycles like it does in Windows XP?  I'm not so sure I can do it from GNOME if I run it from a terminal.  I read through the FAQ on the folding at home website, is there  a command I need to put in before/after the filename to make it run at highest priority?  I checked the usage with the "system manager" or whatever it's called and it's only using like 1-2% of the CPU power.  

Help would be greatly appreciated.[/quote]

Doesn't sound like it's working as it's designed to. Even if it's using "nice value 19" which is the lowest priority for process, it should use all space CPU cycles. Does it download working units?
```

[05:20:44] Working on Unit 01 [November 8 05:20:44]
[05:20:44] + Working ...
[05:20:44]
[05:20:44] *------------------------------*
[05:20:44] Folding@Home PMD Core
[05:20:44] Version 1.03 (September 7, 2005)
[05:20:44]
[05:20:44] Preparing to commence simulation
[05:20:44] - Looking at optimizations...
[05:20:44] - Created dyn
[05:20:44] - Files status OK
[05:20:44] - Expanded 88818 -> 563401 (decompressed 634.3 percent)
[05:20:44]
[05:20:44] Project: 1850 (Run 59, Clone 2, Gen 14)
[05:20:44]
[05:20:44] Assembly optimizations on if available.
[05:20:44] Entering M.D.
[05:20:50] Protein: p1850_Myosin6_PT_US
[05:20:50]
[05:20:50] Completed 0 out of 500000 steps  (0%)
```

If you didn't already try, try reinstalling - consider trying 5.04 version:
[http://folding.stanford.edu/download.html](http://folding.stanford.edu/download.html)

---

### Post by el barto on 2005-11-08
it's working, just at a low priority.

Current Work Unit
-----------------
Name: p1850_Myosin6_PT_US
Download time: October 26 16:26:55
Due time: December 17 16:26:55
Progress: 4%  [__________]

I am using version 5.04.  I am using Gnome and set it at the lowest (most negative) nice value.  No idea why it's not working at full CPU load.  I have the kernel set up to use AMD k8 processor because I have an AMD 64 3500 + could this be a problem?
Also when I use the system monitor the "system monitor" itself is the highest CPU resource hog, but it also shows 100% CPU usage, but the total amount of CPU usage isn't even close to 100% if you total up all the processes, it's like 15% maximum

---

### Post by heimo on 2005-11-08
If you open terminal window and use *top, *how does it report CPU usage? Mine was 100%, folding client 80-90 with nice priority at 19.

---

### Post by el barto on 2005-11-08
[QUOTE=heimo]If you open terminal window and use *top, *how does it report CPU usage? Mine was 100%, folding client 80-90 with nice priority at 19.[/QUOTE]

I did that and now it's reported as 99%.  System Monitor still shows it < 1%.
Also, my temps are WAY down compared to windows, like it's not using ALL the CPU power, but it's still top priority.  Does that make any sense?

What would count for the discrepancy between system monitor and TOP?

---

### Post by RAOF on 2005-11-08
It's highly likely that your CPU is being frequency-throttled.  Powernowd (by default) doesn't count nice'd processes when it calculates processor load.  That accounts for the reduced temperatures.

---

### Post by el barto on 2005-11-08
[QUOTE=RAOF]It's highly likely that your CPU is being frequency-throttled.  Powernowd (by default) doesn't count nice'd processes when it calculates processor load.  That accounts for the reduced temperatures.[/QUOTE]

Well I went into the terminal and used "sudo powernowd -n" command and I still don't see an increase in the temperatures.  Is there a way to check the CPU speed I'm currently running at?

---

### Post by heimo on 2005-11-08
Which priority (nice) is your client running? 0 is normal, 19 is lowest priority, anything below 0 must be set as a root. You can renice processes using... *renice*. (renice [priority] -p [pid], where [pid] is process id) Or you can prefix any command with nice. (nice -n [priority] command) priority is from -20 to 19

---

### Post by RAOF on 2005-11-08
[QUOTE=el barto]Well I went into the terminal and used "sudo powernowd -n" command and I still don't see an increase in the temperatures.  Is there a way to check the CPU speed I'm currently running at?[/QUOTE]
You can add the "Frequency Scaling" applet to the Gnome panel.

---

### Post by el barto on 2005-11-11
Thanks, where can I find this applet?  And does it just let me know the frequency or can I actually adjust it?  I'm at work, shhhh don't tell anyone I'm on the forums!

---

### Post by pataphysician on 2005-11-11
right click a panel and choose "add to panel...," then from te menu that pops up, select cpu frequency scaling monitor. this only lets you see what freq the cpu is running at, it doesn't let you actually manipulate anything. to stop frequency scaling i think you need to do *killall powernowd*

---

