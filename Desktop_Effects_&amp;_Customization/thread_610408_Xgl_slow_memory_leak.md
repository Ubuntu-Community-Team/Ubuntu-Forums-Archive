---
title: "Xgl slow memory leak"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by loso on 2007-11-11
I've noticed that if I leave my computer running for a long time, Xgl slowly creeps up to use over 300Mb of memory!  I get the feeling that this is some kind of memory leak, and I was hoping that someone might know how to fix it...

I'm not sure if this matters, but my computer uses an ATI graphics card.

---

### Post by adarkenigma on 2007-11-12
i can vouch for this occurrence... i wasn't certain why only 500mb was free out 2 gb of ram if i leave computer on for 2 days. i have definitely seen xgl's footprint getting bigger over time. i am no ubuntu expert but my un-scientific study shows that xgl eats lots of ram. hope someone has solution for this.. i also am ATI graphic card holder. (X1400)

---

### Post by Rinzwind on 2007-11-12
I will test this today (have an X300 in my laptop) and see if this is a reason for some unexplained crashes I sometimes have (my lappy seems to crash after 2 hours of usage or so).

---

### Post by Rinzwind on 2007-11-12
3 hours of XGL running and the memory did not go above 65 Mb

administration -> system monitor.
mark XGL
rightclick
memory maps.

See if you can find the culprit :)

---

### Post by loso on 2007-11-13
/dev/dri/card0  is taking up 128Mb
[heap] is taking up 54Mb
and some unnamed thing is taking up 34Mb

so what does this all mean, and what should I do?

---

### Post by hardwear31 on 2007-11-15
My laptop has an ATI card and wouldn't run Compiz-Fusion under Gutsy. Following online advice, I installed XGL a few minutes ago. But when I started an XGL session, it took up 50MB of RAM and in 15 minutes, it has climbed up to 76MB. There is definitely something fishy going on.

---

### Post by Jouke74 on 2007-11-15
I've seen it go up to 200 Mb, but at certain time it seems to stop eating more memory. In my opinion it depends on which programs you have opened. More programs and windows, more memory. This memory does not however seems to be returned to Linux straight as soons as the program is stopped. That might be because the XGL server caches stuff for speed, or it is simply a bug. I never found out. 

I own a ATI X1600, but I don't think the videocard will matter much. It's simply the fact that Nvidia and Intel users will probably run Compiz effects with AIGLX instead of XGL. XGL is only required by the newer ATI cards to run Compiz.

---

### Post by kaustubh on 2007-11-19
My desktop also eating up lots of memory for Xgl and emerald. I m using compiz over gutsy. Whenever i start compiz the Xgl usage is not so high. But after some time its goes above 150mb. Also the emerald shows around 4 Gb of memory usage. There is heave memory leak in both applications i guess. Any one know how to handle this? Attaching the screenshot.

---

### Post by gamma on 2007-12-02
Xgl is more responsive compared to AIGLX on my system so I want to keep using it, but the memory leak is getting annoying. 47% of my memory is going to it right now (400MB ram and 400MB swap). Hopefully they fix this..

---

### Post by Jaymac on 2007-12-02
/dev/dri/card0 is the culprit on my machine as well.  Currently using 128MB.

---

### Post by tommy (8=X on 2008-01-24
i was having the memory leak problem. 

however, today i uninstalled Emerald and it seems to have gone away. 

after hours of use and many window openings and closings (usually enough to bring compiz.real up to about 47% memory use after only a couple hours) compiz.real is still sitting at 4.8% instead.

fingers crossed it stays that way.

could Emerald be the culprit not compiz itself?

---

### Post by Dante1 on 2008-03-14
I have a huge problem with this. As soon as ubuntu starts the system monitor shows XGL is using 130MB and now after 10-11 hours XGL is using 353MB. dri/card0 is using 255MB. Overall memory usage is 780MB...
Look at that!!

---

### Post by jmachacek on 2008-03-28
Notice how everyone's /dev/dri/card0 tops out at 64MB, 128MB, 256MB, etc?  The driver's accessing the card's memory directly and the resource monitor's reporting this as used memory.  E.g. ,if you have a 128MB video card, /dev/dri/card0 is probably showing 128MB usage.  It shouldn't be affecting your actual physical RAM usage.

---

