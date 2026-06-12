---
title: "What is your 'events/0' CPU load?"
date: 2009-03-12
forum: General Help
---

### Post by tbraun on 2009-03-12
After booting into Gnome (on Ubuntu 8.10) and before starting any applications, I run 'top' to see the current processes. I find to my surprise that the 'events/0' process tends to be right up there at the top, with around 3% to 4% of CPU usage.

Is this normal? What do you see for your 'events/0' process?

My understanding is that 'events/0' is used to handle an event queue for the kernel (correct me if I'm wrong, please). But I'm wondering what's there to process when I really don't do anything? Ok, the usual set of applets are there, a graphical clock is ticking, etc. But should this cause 3-4% of CPU load just in the events/0 process alone? No other process uses as much CPU.

Is there a way to check what kinds of events this process is dealing with? Some way to profile or debug this? Is this level of CPU load normal for 'events/0'?

Thank you very much...

Tom

---

### Post by DeMus on 2009-03-12
> **tbraun said:**
> After booting into Gnome (on Ubuntu 8.10) and before starting any applications, I run 'top' to see the current processes. I find to my surprise that the 'events/0' process tends to be right up there at the top, with around 3% to 4% of CPU usage.

Is this normal? What do you see for your 'events/0' process?

My understanding is that 'events/0' is used to handle an event queue for the kernel (correct me if I'm wrong, please). But I'm wondering what's there to process when I really don't do anything? Ok, the usual set of applets are there, a graphical clock is ticking, etc. But should this cause 3-4% of CPU load just in the events/0 process alone? No other process uses as much CPU.

Is there a way to check what kinds of events this process is dealing with? Some way to profile or debug this? Is this level of CPU load normal for 'events/0'?

Thank you very much...

Tom

With me on Ubuntu 8.4.2-64bits the process events/0 is using 0% of the cpu. What kind of CPU do you have? If it's an older "slower" type then even the simplest processes take some percentages already. The faster and more capable processors use less percentages for these processes. I have a Q6600 running on 3GHz so it's probably no wonder why it's on 0% for the mentioned process.

---

