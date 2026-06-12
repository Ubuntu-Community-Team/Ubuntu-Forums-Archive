---
title: "Why is Xorg/compiz eating all my CPU and Memory?"
date: 2011-05-22
forum: Desktop Environments
---

### Post by erissiva on 2011-05-22
I recently reinstalled Ubuntu 11.04 Natty after a massive hard-drive failure.

Now, for some reason, compiz and Xorg decide it's a fun idea to start eating up my RAM and CPU - GB by GB. Starts out at normal amounts, but quickly balloons to 1-2+GB and starts using most of my CPU. This never happened before...but none of my hardware has really changed. The only difference being that I installed 11.04 cleanly, whereas before I had upgraded from 10.10.

For example: Rebooted my computer last night. Xorg using ~90MB RAM, compiz using around the same. Only program running is Transmission. Come back this morning - Xorg is using 1.5GB RAM and over 50% of my CPU and compiz is ~200MB RAM usage. There is NOTHING else running or installed. I haven't activated any fancy Compiz plugins at all, and am running a pretty standard 1-monitor setup. Nothing fancy at all. What gives??? This is insane!

I'm running 11.04 on a 4x AMD Athlon(tm) II X4 640 Processor with 8GB RAM. I'm using the integrated ATI Radeon HD3300 GPU with the AMD Catalyst 11.5 driver - but this problem occurs with the 11.4 AND built-in fglrx drivers as well.

I can give any other logs or sysinfo that is needed. Been using Ubuntu for 4 years now, and have never seen anything as bad as this.

---

### Post by AlmoG on 2011-06-05
I have the same problem with my 11.04
There is a bug report around it somewhere... can't find it atm.
there is a workaround that seems to work for me:

alt+f2 to open a command line
```
unity --replace &
```

this will not log you off or close your applications but it will reduce the memory to a normal size
I would recommend saving your work though... ;)

---

### Post by erissiva on 2011-06-05
**AlmoG** - Thank you for that command! That certainly helps with the Unity memory issue, but Xorg doesn't restart or go down at all. It just keeps going up steadily. I did NOT have this problem in 10.10.

Yesterday Xorg was using 2.8GB of my RAM and 24% of my CPU...and there wasn't anything being displayed. No games, animation, 3D effects, etc, etc. I'm seriously using a completely out-of-box, minimal desktop setup. Nothing fancy at all.

I'm pretty sure Xorg isn't supposed to be using so much RAM and CPU.

---

### Post by BrandonBan6 on 2011-08-15
Same issue happening here.

---

### Post by dining_philosopher on 2012-01-22
My xorg is consuming 7 gb ram and 24% cpu.

Ubuntu 11.04 amd64, gdm 2.32.1-0ubuntu3.2, xorg 1:7.6+4ubuntu3.1, nvidia 270.41.06-0ubuntu1, no unity.

core i3-530, 16gb ram, nvidia gt240 512mb.

Changing compiz to metacity with compiz icon takes no effect.

xrestop - Display: :0.0
          Monitoring 104 clients. XErrors: 331
          Pixmaps: 1262286K total, Other:     626K total, All: 1262913K total

---

