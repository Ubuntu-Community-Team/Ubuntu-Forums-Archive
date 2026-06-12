---
title: "Processor going 100% for no reason?"
date: 2005-03-16
forum: Desktop Environments
---

### Post by silentstriker on 2005-03-16
I have an NC6000 laptop (2ghz, 512mb ram).  When the screensaver comes on and then off, the processor goes to 100% and stays there, until I restart.  It is difficult to do anything, including moving mouse because processor is running.

I do ps -aux, and it doesnt show any process thats taking up that much CPU time.


Please help!

---

### Post by Qdlaty on 2005-03-16
how about *top*
I'm sure it will tell you who's responsible ;-)

---

### Post by silentstriker on 2005-03-16
Nope, TOP is just like the monitor that comes with GNOME.  The highest it displays is a process taking up 12%...and all the rest are basically zero's.


Yet, my computer becomes slow and gnome says processor 100% in use.  However, if I double click on it, it cannot show me a process thats taking up that much processor.

---

### Post by Qdlaty on 2005-03-16
I had the same issue with my laptop but it was ACPI fault. My powersupply cord was damaged and it wasn't  powering continiously.
But this is not a solution.
A tip is, maybe you need to check if there are some extra settings that will run with xscreensaver?

---

### Post by ManiacMac on 2005-03-16
Ok, well I have a NC8000 and Warty would always go apesh*t after a while (ACPI would freak out).

Hoary fixed the issue entirely, but as a quick fix, run the following:

sudo renice 20 5

That aught to reprioritize the kacpid proccess to 19 or so.  The machiine should come back after this, but your proc will still be pegged.  Worked for me until I got all of my data off.

---

