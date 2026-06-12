---
title: "Dual Cores running 100%"
date: 2011-07-30
forum: Desktop Environments
---

### Post by Geffers on 2011-07-30
I have a HP laptop with an AMD Athlon X2 Dual Core QL-65 and an ATI Radeon card running Ubuntu 10.10

When I run a video file using Movie Player (or VLC) through the HDMI output to my TV the 'System Monitor' indicates that both processors are running at around 100% with the fan running continuously.

Would this be normal?

Geffers

---

### Post by wildmanne39 on 2011-07-30
Hi, it could be the with programs you have running on that system.

You can type top into the terminal and see what is using all the cpu, it may be something that is not working right causing the problem or just a lack of resources.

---

### Post by Geffers on 2011-07-31
> **wildmanne39 said:**
> Hi, it could be the with programs you have running on that system.

You can type top into the terminal and see what is using all the cpu, it may be something that is not working right causing the problem or just a lack of resources.

Thanks for very prompt reply, I will monitor with top, I had forgotten about that.

Strangely though after you reminded me of that command I ran a movie using VLC and Totem and each processor is showing around 55%, lot better.

Geffers

---

### Post by docbop on 2011-07-31
video  processing is cpu intensive so that could be your source.  Is cpu pinned or floating around 100%.   Also cpu monitoring tools like top tend to will increase cpu usage with all the I/O the generate. 

Also look and your memory usage and how much swapping is going on.  All that swapping will cause overhead too.  

steve b.

---

### Post by Geffers on 2011-07-31
> **docbop said:**
> video  processing is cpu intensive so that could be your source.  Is cpu pinned or floating around 100%.   Also cpu monitoring tools like top tend to will increase cpu usage with all the I/O the generate. 

Also look and your memory usage and how much swapping is going on.  All that swapping will cause overhead too.  

steve b.

No swapping appears to take place.

Using System Monitor it used to have one processor always showing 100% and the other would be 60-70%, then the processors would swap with similar readings.

Geffers

---

### Post by docbop on 2011-07-31
> **Geffers said:**
> No swapping appears to take place.

Using System Monitor it used to have one processor always showing 100% and the other would be 60-70%, then the processors would swap with similar readings.

Geffers

It's not swapping a lot then its busy with the app(s) and I/O from the app.  Does this go on with just the one app running could be the app is a cpu-hog.  If the cpu isn't pinned at 100% not really a big deal.   

If the app has a support board might want to post there and see if this is a know problem or working as designed for your hardware.

---

