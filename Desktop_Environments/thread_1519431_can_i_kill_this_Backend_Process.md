---
title: "can i kill this Backend Process"
date: 2010-06-28
forum: Desktop Environments
---

### Post by jafarul on 2010-06-28
[IMG]http://img707.imageshack.us/img707/8334/screenshot1bk.png[/IMG]

what is that backend process. its been taking up processes some time up to 78%

---

### Post by husambg on 2010-06-28
yes
in terminal 
sudo top
k (PID) enter
9          enter

I don't know what this process for , it took 99% from my cpu

---

### Post by jafarul on 2010-06-28
thnx. thought abt it before, just cant be sure whether i can kill it or not. im afraid that if i kill this process, my system will go haywire :p

---

### Post by karash on 2010-06-28
> **husambg said:**
> yes
in terminal 
sudo top
k (PID) enter
9          enter

I don't know what this process for , it took 99% from my cpu

Did you by chance run System > System Testing?

There is a bug in Ubuntu (edit: 10.04) that will cause the CPU to skyrocket to 100% once you close the window after System Testing using the process "backend." This doesn't happen during testing, or any step in particular, and can happen even if you choose "Skip this test" all the way through it. And it only triggers once you close the window.

I'm not sure why there hasn't been a fix for this yet, other than to just avoid running System Testing..

---

### Post by husambg on 2010-06-29
Thank you Karash
I was going around ubuntu , so I may did it , I just suddenly found the cpu of laptop and fan going very high and it was from this process.
thank you for explaining this for me

---

### Post by Beta-trefoil on 2010-07-04
I had one of the cores in an AMD Phenon II x6 going at 100%.  Top showed the backend process was the problem, and I had just recently checked out the system testing app.  Killing it solved the probelm, thanks!

---

### Post by lkjoel on 2010-07-04
Also try killall.

---

### Post by kateshine on 2010-08-13
Thanks, had the same issue. Big relief it wasn't something worse going on!

---

