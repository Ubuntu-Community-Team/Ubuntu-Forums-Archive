---
title: "CPU constantly high use"
date: 2009-06-11
forum: Desktop Environments
---

### Post by ajpetersen on 2009-06-11
Trying to use an IBM XSeries 206 server as a desktop machine, Ubuntu 8.10 installed, then upgraded right off to 9.04, found display to be slow, checked 'monitor' and found that the CPU is under a constant load, often as high as 80 > 90% install and everything else up to this point went fine?
Cannot see reason for this problem?
If it had been 'Windoze' I would have thougth virus?

Any suggestions?

---

### Post by asmoore82 on 2009-06-11
use "System Monitor" or `top` to see what is using the CPU.

is compiz running?

---

### Post by Sigurd Suhm on 2009-06-12
I encountered a similar issue and found the Tracker search tool to be the culprit. Apparently when it starts indexing it can get really heavy. As mentioned you could check 'top' to see if that's the case. And if so you can simply remove Tracker. I never used it anyway.

---

### Post by dE_logics on 2009-06-12
Yeah that tracker search utility take up the CPU for indexing...if you have a large HDD having lots of files, it will take a long time to index.

You can disable is at startup in

system>prefferences>sessions>startup.

You can see the tracker applet there...just uncheck it.

---

### Post by ajpetersen on 2009-06-21
Thanks for the advice, sorry not to have been back on to reply till now...
I am very new to Linux as such, I have been suing it for about a year, but just that, not gone into any details as it did just as I wanted on my old machine.

But I have done as advised and found that it is XORG that is using all of the CPU time, it seems it may be something to do with the IBM use of ATi graphics built in?

Please any suggestions?

---

