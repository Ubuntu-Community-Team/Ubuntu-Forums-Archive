---
title: "Just upgraded RAM (what now)?"
date: 2005-12-14
forum: General Help
---

### Post by Mr. Electric Wizard on 2005-12-14
I just went from 256 to 512 megs of RAM in my Laptop last night, but then I realized that I really don't know if the new memory got picked up by Breezy or not.
In windows I used to go to MyComputer, Properties and it told me how much memory was installed...

When I look in Breezy I see swap memory and system memory.  I am guessing that the sum of system + swap is the amount of total memory right?
Do I need to do anything else?

---

### Post by M3ta7h3ad on 2005-12-14
Providing you dont have over a gigabyte of ram you will not need to do anything once its in (aside from maybe a few bios option tweaks :)). Do a cat /proc/meminfo just to make sure its been picked up.

Mine results in...
> 
m3ta7h3ad@redemption:~ $ cat /proc/meminfo |grep "MemTotal"
MemTotal:      1556640 kB


I have 1.5Gb of ram, so the above figure is right :)

---

### Post by Mr. Electric Wizard on 2005-12-14
Exactly what I was looking for.
Thanks!

---

### Post by Robocoastie on 2005-12-14
swap memory is a partition on your hard drive that the system uses (in windows its called cache) for temporary fast retrieval. When you have a lot of RAM it'll rarely actually use the swap space.

---

### Post by ninotob on 2005-12-14
You can also get this info with the command "top", along with actively updated data on used and free memory, how much your system is using the swap space, cpu activity, and the top current hogs of your system.  Press "q" to quit top.

---

### Post by Mr. Electric Wizard on 2005-12-14
Interesting.
I just put a second 256 meg stick of ram in my Laptop, which supposedly already had a 256 meg stick in it.
I was fully expecting a whopping 512 megs after putting in the second stick.
What shows up in Top is 384 megs?
Very interesting.

I guess what I will try is to put one stick in at a time and see which one is the imposter!:mad:

---

### Post by ninotob on 2005-12-15
Is the ram shared with your video card?  I don't have a laptop that uses shared ram but I would imagine there is a bios setting related to that.

---

