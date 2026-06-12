---
title: "What is tying up my CPU ?"
date: 2008-05-13
forum: Desktop Environments
---

### Post by Kumera on 2008-05-13
I have a little System Monitor box in the top panel of my Ubunty Hardy, which frequently tells me that my processor is running at 100% capacity.  At such times, computer response is quite sluggish.  If I load up the full System Monitor (usually by double clicking the little box in the panel), and go to the processes tab, I can click on the CPU column to see what System Monitor thinks is using my CPU.  But, it rarely gives me a full story.  Usually I get something like Firefox - 26%, Gnome System Monitor - 9%, Gnome Panel 2%, and that is it.  Everything else in the list is given at 0% of CPU capacity.  What is using the other 63% of my CPU capacity?  What else can I use to find out?

---

### Post by NightwishFan on 2008-05-13
Open a terminal and type:
```
top
```
It will list processes in order of used cpu.

---

### Post by L8erG8er on 2008-05-13
If you're running Firefox 3b5 that came with Hardy Heron, it's probably that.  I know in my case, Firefox is periodically running my hard drive to death, and everything else is slow until it's done, usually about 15-20 seconds.

---

### Post by mokshadaya on 2008-05-13
I have to concur regarding FireFox 3b5.  I have similar issues, along with others.  Besides using Top you might try using PowerTop to get a full view of what's processing.  This has proven itself to be a very useful utility for me.

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by BlueSkyNIS on 2008-05-13
Maybe checking "View -> All processes" in System Monitor will help?

---

### Post by BlueSkyNIS on 2008-05-15
There is a known issue with the System Monitor, use TOP or alternative. I think fix for the System Monitor is in progress, check [https://bugs.launchpad.net/gnome-system-monitor/+bug/93847]("https://bugs.launchpad.net/gnome-system-monitor/+bug/93847")

---

### Post by Kumera on 2008-05-16
OK - thanks all.  Using "Top" worked - it seems that the culprit CPU hog was primarily Apache, ticking away in the background.

---

