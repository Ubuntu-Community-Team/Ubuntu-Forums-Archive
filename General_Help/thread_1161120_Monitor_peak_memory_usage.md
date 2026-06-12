---
title: "Monitor peak memory usage"
date: 2009-05-16
forum: General Help
---

### Post by XCan on 2009-05-16
I'm curious as of how much mem I use when I do my daily stuff on my system. Is there any simple way to monitor the peak memory usage of my Ubuntu system? I'm kind of referring to the peak memory usage as displayed in, for example, Windows' process manager.

In short, I'm looking for a script or program that can track the memory usage and when asked, display the peak number. :)

---

### Post by compnut41 on 2009-05-16
System>Administration>System Monitor

Shows everything in a live feed, very nifty.

Terminal command xload:

Shows the load on the computer updates every 10 seconds. (can be customized)

---

### Post by XCan on 2009-05-16
Thanks for the answer compnut41. However, I'm only interested in the peak load and not monitoring them manually. :)

---

### Post by donato roque on 2009-05-16
You might try opening the terminal and then type:
free -m <return>

This will display your memory usage and swap in 
megabytes.

---

### Post by XCan on 2009-05-16
Thanks, I'm mostly using 'free' already. I think my question was a bit ill-formulated.

What I'm looking for is a script or program that can track and log my memory usage, and when asked display the peak memory usage according to its tracked record. Perhaps it's doable using a scirpt by periodically taking the output of free and log it? Unfortunately, I've no idea how to proceed to write such a script. :(

---

### Post by XCan on 2009-05-17
*bump*

---

### Post by XCan on 2009-05-18
*bump*

---

### Post by dcstar on 2009-05-18
> **XCan said:**
> Thanks, I'm mostly using 'free' already. I think my question was a bit ill-formulated.

What I'm looking for is a script or program that can track and log my memory usage, and when asked display the peak memory usage according to its tracked record. Perhaps it's doable using a scirpt by periodically taking the output of free and log it? Unfortunately, I've no idea how to proceed to write such a script. :(

Synaptic-Search-"resources" : atsar

---

### Post by XCan on 2009-05-18
Many thanks dcstar! Trying it out now! :)

---

### Post by XCan on 2009-05-18
I installed astar, however, I'm uncertain how this should be used. If I try to run it I get,
open /var/log/atsar/atsa18: No such file or directory,
so I took a look in [http://manpages.ubuntu.com/manpages/intrepid/man1/atsar.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/atsar.1.html). But I'm still uncertain how to make it work, the man page also refers to atsadc. Do I have to use that in the end to tell atsar to run and collect data?

---

### Post by sourchier on 2009-05-18
You could try Munin. There web site is
code:
http://munin.projects.linpro.no/

Try 
code:
apt-get install munin

to install it.

---

