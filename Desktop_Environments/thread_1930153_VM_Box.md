---
title: "VM Box"
date: 2012-02-23
forum: Desktop Environments
---

### Post by ericgahn on 2012-02-23
Good day all;
 
I would liek to set up a desktop box as a VM box running Ubunutu as host OS with VM's running Windows (XP/7) and Ubuntu. These could be running simultaneously.
 
I want the host OS to be as small as possible so that it does not consume much memory from the machine. In this respect I would appreciate if someone could help me with the following:
 
1) Is an i5 processor adequate for this?
 
2) How much memory? I was thinking 6-8Gb (1 to 2 for host OS, 2 each for guests).
 
3) How would I install Ubuntu (and what flavour of it) as host to consume minimal resources from hardware?
 
4) What is the best option for a VM platform in Linux? (On Windows I use VMWare and Microsoft VirtualPC but I know other alternatives exist).
 
Thank you for all and any help provided.
 
Eric

---

### Post by cybergalvez on 2012-02-24
easliy done, I do it myself all the time.
1) i5 should be sufficent, although I would not assign more than 2 processors to any given vm
2) memory is going to be your bigest limiting factor, if you want to run 2 vm plus your host I would stick with 8 gig
3) the amount of memory ubuntu uses really depends on how you intent to run it. If you want a gui, stick with either xubuntu or lubuntu both very light on resources. if you want to run them as services that you connect to like via RDP from another machine, it really doen't matter since the gui won't be running anyway.
4) I like virtualbox, but vmware is also very good, I guess it's all personal preference. I've run virtualbox and had a headless windows set up that I connect to via RDP works very well, I've also has several OS's running at the same time each in a different window so vbox can easily handle what you want.

Good luck

---

### Post by ericgahn on 2012-02-26
> **cybergalvez said:**
> easliy done, I do it myself all the time.
1) i5 should be sufficent, although I would not assign more than 2 processors to any given vm
2) memory is going to be your bigest limiting factor, if you want to run 2 vm plus your host I would stick with 8 gig
3) the amount of memory ubuntu uses really depends on how you intent to run it. If you want a gui, stick with either xubuntu or lubuntu both very light on resources. if you want to run them as services that you connect to like via RDP from another machine, it really doen't matter since the gui won't be running anyway.
4) I like virtualbox, but vmware is also very good, I guess it's all personal preference. I've run virtualbox and had a headless windows set up that I connect to via RDP works very well, I've also has several OS's running at the same time each in a different window so vbox can easily handle what you want.

Good luck
Thanks cybergalvez

---

