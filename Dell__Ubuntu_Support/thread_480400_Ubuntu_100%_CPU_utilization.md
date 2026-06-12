---
title: "Ubuntu 100% CPU utilization"
date: 2007-06-21
forum: Dell  Ubuntu Support
---

### Post by TurboPotato on 2007-06-21
Hello,

I recently installed Ubuntu 7.04 fiesty fawn onto my Dell Latitude C640 Laptop.

Everything installed fine and it seems to be running ok except for one thing.

No matter what I do, even if there isn't a single program running I am constantly getting 100% utilization speed on my processor.  There is nothing I can do to make this stop, to make the processor idle at something less then 100%.

I'm totally lost.  Anyone help?

Here are the complete specs for my comp:
Intel Pentium(R) 4 Mobile CPU @ 2.00 ghz
748 Megs of Ram
60 gig harddrive.  48 gigs available.
DVD drive
Ubiquiti atheroes wifi card in a PCMCIA slot.


Thanks!

-TurboPotato

---

### Post by newtimes on 2007-06-21
is this happening only with fawn?
have you tried 6.10 or 7.10(gutsy gibbon) to see if it changes.

---

### Post by Chasoid on 2007-06-21
Try running the "**top**" command.  It should show, in decending order by CPU usage, all of the processes.

While it's running, you can use the "**i**" command to have it not show processes that are idle.

Perhaps that will show the process that's causing your 100% utilization.

---

### Post by cwgpress on 2007-06-21
Other systems I've used that had the same phenomenon were counting time used by the idle task.

---

### Post by mpires on 2007-06-21
Personally I solved my cpu usage problem by changing the value in /sys/module/processor/parameters/max_cstate to the value 1. Seeing that it worked, I inserted a line in rc.local to make this automatic

---

### Post by TurboPotato on 2007-06-22
So.... here's what's happened so far...

I downloaded the htop package to see what could possibly be causing the CPU to constantly spike and cause my computer run like crap....

It seems as if though it "bounces" around.  This is so weird.  When you look at htop you see multipliable different programs takes the place of causing the CPU to spike.  It seems to have kind of just....stopped though.  For awhile it looked like CUPS was causing the problem, but that was changed and I haven't seen much of it lately.

This is one of the weirdest problems I've ever seen.  I think though....that it has something to do with my fans.  Every time my fans kick in, the computer slows to a crawl.  This is weather its on windows or on Linux.  It was recently formatted to just Ubuntu exclusively and it still seems to be doing it.  I've tried changing the fan speed and voltage and still it does the same thing.  I don't get it :(

---

### Post by Tethtibis on 2007-06-27
you might be getting a bad reading, the hardware that checks your cpu speed may not be installed right "the chipset" or ubuntu installed the best match it could find. i had this same issue on my dell latitude d505, and had to break the chipset files from dell to apply the correct modes in ubuntu. but it's just a quirk. it shouldn't hurt anything.

---

