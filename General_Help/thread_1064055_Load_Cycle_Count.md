---
title: "Load_Cycle_Count"
date: 2009-02-08
forum: General Help
---

### Post by vandorjw on 2009-02-08
Hi,

I am wondering what Load Cycle Count is for Hard drives
I did some google-ing to see what is normal and I think mine is way to high.

The drive is about a year and a half old and it is at 228,217
I think I have been a bit to harsh on it maybe?

I am wondering..
a) what is the normal count for a laptop drive that's about 1.5 years old.

and 

b) what is the max before it starts to have problems?


If anyone is interested, I'll attach the output from 
"sudo smartctl -a /dev/sda | more"

Cheers - CC7

PS: I have laptop mode enabled for about a week (I think I am going to disable it) because it continually turns my hard drive on and off about every 2-4 minutes.

---

### Post by vandorjw on 2009-03-24
To answer my own questions: 
A typical hard Drive is good for roughly 600,000 load_cycle_counts

-------------------------
after a couple of months, the load cycle-count has increased by roughly 200.

I have a dell-inspiron 1520. If anyone else also has one, I suggest that in the bios, put the Hard-drive-performance to "performence" (By-pass and Quiet both make the LCC go way up)

---

