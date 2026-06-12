---
title: "System monitor shows 2 cpus in Acer Aspire One"
date: 2009-05-06
forum: General Help
---

### Post by jacktar on 2009-05-06
I have the UNR on my Aspire One. Why does system monitor show 2 processors, each using about 25% when nothing else is running ?

---

### Post by Legace on 2009-05-06
You probably have a Intel Atom processor that supports hyper-threading. For an overview of hyper-threading, go to the following link and click on the "Intel Hyper-Threading Technology": [http://www.intel.com/business/resources/demos/xeon5500/performance/demo.htm](http://www.intel.com/business/resources/demos/xeon5500/performance/demo.htm)

Hyper-threading allows the processor to execute 2 simultaneous tasks at once, so it appears as 2 processors.

I have no idea how network remix works, but don't you have System Monitor somewhere? Check which process takes most CPU usage..

---

### Post by jacktar on 2009-05-06
It's system monitor that shows the 2 cpus. I ran htop and it shows system monitor using about 20-30% and /usr/X11R6/bin/X using another 20-30%. If I close system monitor cpu usage is only about 3%

---

### Post by Legace on 2009-05-06
Then you're fine :)

You don't really have two CPU's. It's just that you have ONE CPU that has 2 threads. In other words, it can process TWO things simultaneously.

That's why the system "sees" it as 2 seperate processors :)

---

### Post by gfe on 2009-05-06
I have an Intel Pentium 4 in my machine, and the system monitor also shows it as having two CPUs.

---

### Post by Legace on 2009-05-06
> **gfe said:**
> I have an Intel Pentium 4 in my machine, and the system monitor also shows it as having two CPUs.

Yes, as it, too, supports Hyper-Threading ;)

---

### Post by jacktar on 2009-05-06
Thanks for the info, I think I'll use htop instead of system monitor.

---

### Post by gfe on 2009-05-06
All very interesting. I knew there had to be a simple explanation.

---

