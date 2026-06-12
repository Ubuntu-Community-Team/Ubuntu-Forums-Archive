---
title: "Does Ubuntu overclock automatically?"
date: 2010-10-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr Tickle on 2010-10-04
Hi all,

With windows 7 I had a little app/gadget that would tell me if my laptop was overclocking automatically. My processsor is an i5 M450 running at 2.4GHZ and overeclocks to 2.67GHZ I believe.  

So does Ubuntu (running Lucid Lynx 10.0.4) automatically overclock my processor if the need arises? is there a program/application that could monitor this?

Thanks

Mr Tickle :)

---

### Post by NickReed on 2010-10-04
No, for sure it doesn't try using NVClock

---

### Post by cascade9 on 2010-10-04
Thats 'turboboost', and its not really 'overclocking'. 

It should run up to 2.66Ghz, but AFAIK none of the standard linux system monitors (etc) pick up turboboost scalling. The intel 'turbostat' and 'i7z' tools should figure out turboboost just fine, and report it accurately. 

BTW, you need kernel 2.6.33 or higher for turboboost to work. Its possible that some distros have backported some of the bugfixes/etc from 2.6.33 into 2.6.32 though, I really woudlnt know. 

> **NickReed said:**
> No, for sure it doesn't try using NVClock

nVclock is for overclocking nVidia cards......its totally useless in this situation.

---

### Post by Mr Tickle on 2010-10-04
Thanks for the replies :)

It's not like I need Ubuntu to automatically 'turboboost' when the demand for my processor gets high as it seems whatever I throw at Ubuntu it doesn't tax the processor that much thankfully. (Excluding Video conversions)

So the whole idea of 'turboboosting' then from what I have ascertained is that the processor is able to clock at that top speed stated (2.67GHZ) but doesn't in order to save power - only increases clock speed when the demand is there. - Is that along the right track?:confused:

Currently I have the 2.6.32-25-generic kernel as stated by the terminal when inputting "uname -r". I'm guessing from your statement cascade9 that 'turboboost' may of not yet been implemented - again not a problem.

Thanks 

Mr Tickle

---

### Post by cascade9 on 2010-10-04
> **Mr Tickle said:**
> It's not like I need Ubuntu to automatically 'turboboost' when the demand for my processor gets high as it seems whatever I throw at Ubuntu it doesn't tax the processor that much thankfully. (Excluding Video conversions)

So the whole idea of 'turboboosting' then from what I have ascertained is that the processor is able to clock at that top speed stated (2.67GHZ) but doesn't in order to save power - only increases clock speed when the demand is there. - Is that along the right track?:confused:

Currently I have the 2.6.32-25-generic kernel as stated by the terminal when inputting "uname -r". I'm guessing from your statement cascade9 that 'turboboost' may of not yet been implemented - again not a problem.

Turboboost only runs on one core at a time, so for video conversion it wont make much difference. 

You've got the idea right. ;) 

Its possible that ubuntu has backported turboboost to kernel 2.6.32, I dont know (and I'm too lazy to go looking LOL).

---

### Post by Mr Tickle on 2010-10-04
Thanks cascade9 for even more information :) 

Mr Tickle

---

### Post by cascade9 on 2010-10-05
No problem, hope it helped ;)

---

