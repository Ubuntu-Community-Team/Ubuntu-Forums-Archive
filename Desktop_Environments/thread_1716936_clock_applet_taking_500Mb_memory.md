---
title: "clock applet taking 500Mb memory"
date: 2011-03-29
forum: Desktop Environments
---

### Post by mybodya on 2011-03-29
I don't think it's good for clock. I think 5kb would be enough for it. So what's up, ubuntu geeks?
[https://picasaweb.google.com/mybodya/Mar292011#](https://picasaweb.google.com/mybodya/Mar292011#)

---

### Post by mcduck on 2011-03-29
You are looking at *virtual memory* usage. :D

That includes all memory shared with other applications, so for example GTK libraries would be included in the virtual memory usage for every application that uses GTK.

Virtual memory also includes data stored on hard drive, and many other things as well. So virtual memory usage doesn't tell you how much running a program would increase your RAM usage.

(for example try counting together the virtual memory counts for all the programs visible on your screenshot. The number would quite likely exceed the amount of physical RAM you have in your computer...  ;))

Edit: If you go to the System Monitor's preferences, you can enable the "Memory" field. This is much closer to the application's actual memory usage, although estimating the exact value is basically impossible (for example it's impossible to determine where to count all the shared memory usage, as it belongs to many applications at the same time).

For a better picture you could of course also enable all the other memory fields (resident, writable, shared and x-server) and estimate the memory usage based on those. But in most cases just reading the "Memory" field should be pretty close to truth.

---

### Post by sakishrist on 2011-03-29
I ... might be mistaken but ... do the "visible" processes only, sum up to 12.5 GB?

By the way, empathy looks suspicious as well.

---

### Post by sakishrist on 2011-03-29
> **mcduck said:**
> You are looking at *virtual memory* usage. :D

That includes all memory shared with other applications, so for example GTK libraries would be included in the virtual memory usage for every application that uses GTK.

Virtual memory also includes data stored on hard drive, and many other things as well. So virtual memory usage doesn't tell you how much running a program would increase your RAM usage.

(for example try counting together the virtual memory counts for all the programs visible on your screenshot. The number would quite likely exceed the amount of physical RAM you have in your computer...  ;))Oh, I see. Thanks

---

