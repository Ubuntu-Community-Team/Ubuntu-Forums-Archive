---
title: "Startup manager Issue"
date: 2009-04-09
forum: General Help
---

### Post by yokohama1970 on 2009-04-09
My issue is with startup manager in 8.10 Intrepid Ibex. It used to work, but now when I try to launch it from system-admin-startup manager it does the "performing pre- configuration tasks" & never launches. What specifics do you need from me? Since it stopped launching, I have removed & re-installed start-up manager several different times, but with the same result. Any advice out there? I have spent weeks searching this forum, other Linux forums & Google for any possible answers. Thank You

---

### Post by jeepmonster01 on 2009-04-09
hey i had the same problem today after installing awn manager; just open a terminal and copy and paste these one at a time:

sudo apt-get remove usplash-theme-ubuntu

sudo apt-get install usplash-theme-ubuntu

this will fix the problem!!!

---

### Post by yokohama1970 on 2009-04-11
Jeep

Thanks for the advice. I had already tried your advice prior to your reply. It always ends up with the "dpkg --configure -a" message, which takes forever & never fixes anything. It is just Start-up Manager & Synaptic Package Manager, I can live without it. I have everything dialed-in on Ubuntu 8.10 Intrepid. Glad to hear that worked for you. Thanks for the reply.

---

