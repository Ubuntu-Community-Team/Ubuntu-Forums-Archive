---
title: "i8kmon Dell XPS M1710 - surging fan speeds"
date: 2008-11-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chadeldridge on 2008-11-13
I am having an issue with my fans surging on and off with the I8k package set to auto.  I have the following configurations:

```
#file:/etc/i8kmon

# Run as daemon, override with --daemon option
set config(daemon) 1

# Automatic fan control, override with --auto option
set config(auto) 1
set config(timeout) 1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# These were tested on the I8000. If you have a different Dell laptop model
# you should check the BIOS temperature monitoring and set the appropriate
# thresholds here. In doubt start with low values and gradually rise them
# until the fans are not always on when the cpu is idle.

set config(0) {{- 0} -1 50 -1 55}
set config(1) {{1 1} 40 60 35 65}
set config(2) {{2 2} 50 70 45 75}
set config(3) {{2 2} 60 128 60 128}

# end of file


```

Fans tend to remain around a constant RPM until CPU hits 60c and then wildly surge up to high speed and then back to low.. .on and off about every 2 second.  I am sure this is not good for the system and it is surely annoying.  What i need is a way to tell the fans not to surge up and down so much... maybe reduce the polling time so they stay in high mode longer and the machine cools more in that period to reduce the amount of up / down. 

Any tips or help is appreciated.

---

### Post by antigona1 on 2008-11-16
I have the same issue on an M1330.. any luck resolving (or at least identifying) the problem?

---

### Post by wecucho on 2008-11-18
The problem is not the i8kmon or dellfand, the problem is the BIOS thats prevent the fan run to high, i have a XPS M1710 with ubuntu 8.10 and this problem its just about to make me crazy, i have no idea until now to solve it... until i found a solution i have a several problem with the heat and the fan control, anyone else know something that could help ?

---

### Post by chadeldridge on 2008-11-18
It looks like you are saying you have a solution.  Is that correct?  Can you share?

---

### Post by wecucho on 2008-11-18
No, i dont have a solution yet, im trying to get this to work right... anyone is invited to colaborate with this issue, btw, im running Ubuntu Intrepid (8.10) 64 bit

---

### Post by chadeldridge on 2008-11-23
For the time being i have just removed the line from the rc.local file that starts the i8kmon with auto fan contrtol and just am letting my BIOS control the fans.  It appears that BIOS only ever turns on one of the 2 fans and its always set to mode 1.  Sigh .. why cant Ubuntu and Dell get this fans stuff right.  I have already ruined 1 laptop because of this horrible fan control system.

Back to just doing it manually for now if i need to do anything intensive:

i8kfan 2 2     (sets everything to high)
i8kfan 1 1     (sets everything to low)
i8kfan 2 1     (CPU fan to full other to low)

---

### Post by chadeldridge on 2008-12-19
I assume no one has found any new info?

---

### Post by bakketti on 2008-12-26
I'm having the same problem with my Inspiron 1420 and Intrepid. The surging started after installing the Nvidia Restricted Drivers. So far, gkrellm and i8k do not fix the surging issue. This is extremely annoying. I did not have this problem with previous Ubuntu installs. Not sure if this is an Nvidia driver issue or an Ubuntu issue.

---

### Post by bakketti on 2008-12-27
I think I solved the problem for my computer. Needed a Bios update. The fans appear to be working as expected now.

---

### Post by chadeldridge on 2008-12-27
Unfortunately I am already on the newest revision of the BIOS for the M1710 and it doesn't help my issue.

---

### Post by wecucho on 2009-03-25
i think is a problem related to i8kmon, cause if i shutdown the monitor (i8kmon) and manually use i8kfan command in a console like this: 

i8kfan 2 2 

The fans start to run in high speed and never shutdown unless i say.. so must be a i8k problem

---

