---
title: "consistant 80-100% 50% cach ram use and 0% swap"
date: 2005-07-07
forum: Desktop Environments
---

### Post by Omnios on 2005-07-07
After months of problems I stumbled appon a performace issue. According to system monitor my ram is always running at 80 to 100% with about 50% of that being cach even when running other programs. The part that got me is that cach is at 0 and stays at 0 not a single tick over the last few hours even when running apps. This would explain the issues I am having with gamming as most are the same games I run in XP with no problems "and dont say use windows or ill Flame you". Anyways does anyone else have the same problem of know of a fix? 

 Id would really know how to fix this before my ibm think pad comes which will also run Ubuntu.

---

### Post by alastair on 2005-07-07
In Linux, unused memory is wasted memory. The rationale being - why have "free" memory?

Post an example output of "free".

---

### Post by Omnios on 2005-07-07
Let me put what I read in pount form.

 My computer seems not to use swap period even when processor and ram are at 100+ it bogs slows down making reasonable gamming impossible because the computer bogs down and lags terribly even with low requirment gamming.

---

### Post by byen on 2005-07-07
this is not a solution but might be something you might wanna look into.. are you running too many applications? especially Evolution? I run evolution and all its applications put together, it takes up over 200mb...
evolution 2-2 - 71.7mb
evolution alarm notify - 68.7mb
evolution data server 77.8mb
evolution exchange server 32.2 mb

and a whole lotta cpu space...so check if that is running...? maybe if you disable it..somethin might work out. I love evo so have to put up with it. If you dont need it pull it out!
this is not a solution for the question you asked but might help gettin the mem usage down.
goodluck.

---

### Post by alastair on 2005-07-08
You might have a problem. But maybe the OS is not at fault, just your games. Who knows. As I said, show some detail e.g. free.

My desktop here (1 GB RAM) has :

```

[alastair@persephone license]$ free
             total       used       free     shared    buffers     cached
Mem:        904792     893340      11452          0     274108     127292
-/+ buffers/cache:     491940     412852
Swap:      2056312     946288    1110024

```

Not much free, lots of swap used. I'm not disturbed by this. If I do something memory hungry (like compile a large program), other things go slow (like switching to a desktop and firefox).

Another useful command : ps axl

See what's using your RAM.

---

### Post by Omnios on 2005-07-09
```
tom@Main:~$ free
             total       used       free     shared    buffers     cached
Mem:        256792     250560       6232          0       7596      61336
-/+ buffers/cache:     181628      75164
Swap:       746980      23008     723972
``` 
 
for some reason today swap decided to work 5%. Not running anything special just firefox browser and the desk top. Just about all the games I play require a min of 256megs ram so I was getting worried.

---

### Post by Omnios on 2005-07-18
Think I figured it out not 100% shure but thought of what stuff I loaded when when this performance issue fist started and when't though system monitor and found that clam used huge amounts of ram. Anyways I uninstalled Clam anti virus and my ram whent way down almost to half of what it was. Now its running at about 50% of what it was. I dont like giving up clam but found the  computer responded quicker after uninstalling it also my Never winder Nights game was almost playable but still gittery. 

 Now I have to track down whats periodicly running causing my game to become unplayable. This isn't just about freeing ram its about making my computer run proper and being able to play games I used to play in Linux without these problems. The first time I installed Never Winter Nights in Linux it ran smother than in windows and now its all fubar, I even changed my color depth to 16 in desktop to make things run quicker in destop and that gave me a huge gain for a couple days than things got all fubar again. Now I have to figure out why my network is periodicly running at 30 to 40% when not accessing the internet.

---

### Post by lassel on 2005-07-29
[QUOTE=byen]this is not a solution but might be something you might wanna look into.. are you running too many applications? especially Evolution? I run evolution and all its applications put together, it takes up over 200mb...
evolution 2-2 - 71.7mb
evolution alarm notify - 68.7mb
evolution data server 77.8mb
evolution exchange server 32.2 mb

and a whole lotta cpu space...so check if that is running...? maybe if you disable it..somethin might work out. I love evo so have to put up with it. If you dont need it pull it out!
this is not a solution for the question you asked but might help gettin the mem usage down.
goodluck.[/QUOTE]

How did you disable the evolution servers?

I don't know what they do. I don't run evolution and I kinda assume that they don't do anything I will miss.

---

