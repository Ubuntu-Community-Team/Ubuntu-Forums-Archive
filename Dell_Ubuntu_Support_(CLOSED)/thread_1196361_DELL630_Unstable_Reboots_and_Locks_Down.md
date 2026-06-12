---
title: "DELL630 Unstable Reboots and Locks Down"
date: 2009-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by malabito on 2009-06-24
Dear Forum Members, 

Will really appreciate your advice on the following topic, i used to use ubuntu 7.X on an inspiron 9300 but after having so many issues with wireless driver disappearing i decided to go back to windows. A friend of mine spoke so highly of this version that i decided to give it a try, its sure a great improvment, but i still have some issues to solve which have make my experience a headache, will like to try to solve them before going back to windows.

I have a DEL630, i have read a lot about the intel graphics issue but mine seems to be smooth on the graphics department, also had some issues with no audio so i downloaded the pulse audio which seem to solve the issue.

Whats givingme me a huge headache are the constant lock downs and resets. In the constant lock downs, their is actually nothing i can do, the whole computer freezes, their is nothing that i seem to be doing that triggers this issue. Sometimes the screen goes black a huge amount of color static noise is seen and suddenly the computer just logs me out or reboots.

All your advice will really be appreciated I am not an expert on linux, but i am eager to learn.

Thanks and best regards.

---

### Post by coffeeaddict22 on 2009-06-25
Hi,
Sounds like you may have a graphics problem after all, although it could be anything.
A good place to start would be to look in the system logs.  typing ```
dmesg
``` in a terminal will print out what the kernel's been up to; if there's a crash you should see something in there. Another place to look is in System/Administration/Log file viewer.  If you look in one of those spots immediately after rebooting from a crash, you should be able to see where the problem lies.

Secondly, do you have the Intel driver that's the problem?  Can you post back the output from ```
lshw -C display
```

Post back if you need more help.

---

### Post by malabito on 2009-06-25
Mr Coffe thanks for taking the time to reply here is the output, it seems i do have the intel problem with the video card:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

Will try looking at the log files next time it reboots or hangs up.

Thanks

---

