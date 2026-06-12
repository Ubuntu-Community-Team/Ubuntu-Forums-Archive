---
title: "System Monitor Processes and Resources tab not the same amounts."
date: 2009-06-17
forum: General Help
---

### Post by giga_user_66 on 2009-06-17
Hi there,

I have been using Ubuntu (32bit) since 8.04 came out. I run 9.04 now.
I have a Q6600 CPU, 4 gigs of ram and raptor as system disk.
Inside Ubuntu I have a Virtual Machine running, XP. Please note that both with or without the VM activated it takes a little more than a week before Ubuntu starts eating more memory than the total amount of MB shows up in the System Monitor tab "Processes"
Since I use Munin to keep track of these things I noticed this pretty fast..

Here is a picture of my memory usage in this month:
[IMG]http://img199.imageshack.us/img199/9940/memoryusage.jpg[/IMG]

As you can see the memory used for "apps" rises each day.
When I open system monitor I check the Processes tab and if I sum all those MB's up I am still far away from the 1.2 G it says its currently using. However the "Resources" tab does say it is using 1.20 G. (just like the Munin graph does)
I have never been able to understand why this green block keeps on rising in my graphs and if it is dangerous.

Hopefully someone here can help me explain why this is happening.

---

### Post by regala on 2009-06-17
> **giga_user_66 said:**
> Hi there,

[snip]

As you can see the memory used for "apps" rises each day.
When I open system monitor I check the Processes tab and if I sum all those MB's up I am still far away from the 1.2 G it says its currently using. However the "Resources" tab does say it is using 1.20 G. (just like the Munin graph does)
I have never been able to understand why this green block keeps on rising in my graphs and if it is dangerous.

Hopefully someone here can help me explain why this is happening.

this can mean some apps you run have memory leaks.
try and monitor every day which apps have their amount of memory raised regularly. be sure to seek for resident memory and not virtual memory.

---

### Post by giga_user_66 on 2009-06-17
I did that before. But none in my list of "processes" do this. My vmx used to grow each day but then it seems to come to a tipping point and goes back to a small size again. Yet that green line keeps growing. So something else not visible keeps causing this..

---

### Post by giga_user_66 on 2009-06-18
Anyone with ideas?

---

