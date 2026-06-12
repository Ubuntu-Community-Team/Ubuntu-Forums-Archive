---
title: "What is the gnome-system-monitor virtual memory column?"
date: 2011-06-16
forum: Desktop Environments
---

### Post by chmac on 2011-06-16
I'm looking at the output of `free -m` and top and gnome-system-monitor.

I can't figure out what the "Virtual Memory" column means. I can see the following columns:
* Virtual Memory
* Resident Memory
* Writeable Memory
* Shared Memory
* X Server Memory
* Memory

As far as my research goes, virtual memory is memory overflow on disk (swap space). However, looking down the virtual memory column in gnome-system-monitor quickly adds up to waaaay more than the 3.9GiB of swap space I have. In fact, it quickly adds up to more than my total physical plus swap.

So what does this column actually mean? And when I see that nautilus is apparently using 1.2GiB of Virtual Memory, should I worry?

I've noticed all this because I frequently don't have enough free swap space to hibernate my machine since upgrading to 11.04. It was a problem I never saw on 10.04 with the same 4GiB RAM / 4GiB swap.

---

### Post by amauk on 2011-06-16
Virtual memory is the amount of memory that the process has access to
This can be a little confusing, as memory management is rather complicated, and the virtual memory value is not really that relevant in most cases

Virtual memory is the total of the processes resident memory, any shared memory that component libraries share, and any memory mapped files the process may have opened

Almost all programs will have a larger virtual memory size than resident memory, as the standard C library exports some shared memory to programs

Just because Nautilus has access to 1.2GiB of memory, does not mean it's "using" 1.2GiB of memory

---

### Post by chmac on 2011-06-17
Ok, that's starting to make some sense, thanks amauk. Does one of the numbers tell me how much swap is being used by a process? Or how much the total swap plus physical is in use? (I could calculate swap by deducting physical from that figure).

I find that after a week or two, my system is using about 1.5GiB - 2GiB more memory than at boot time, with the same applications running. I'm trying to isolate where the memory is being used so I can hibernate successfully (and generally improve performance).

---

### Post by Kangarooo on 2011-11-08
I also want to find how much swap is using ot adjust swappiness

---

### Post by chmac on 2011-11-08
I believe you'll get a good idea of swap usage from `free -m`. That will tell you how much swap you're using. I was once told by a db admin that the key line is the second one, the memory usage +/- buffers & cache, because that's how much memory you're actually using, the rest is being used by the OS because it's free. At least that's my simplistic understanding of it. :-)

---

