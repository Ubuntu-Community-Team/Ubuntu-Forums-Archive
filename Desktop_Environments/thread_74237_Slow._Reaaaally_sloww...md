---
title: "Slow. Reaaaally sloww.."
date: 2005-10-11
forum: Desktop Environments
---

### Post by viniciustp on 2005-10-11
I have a AMD Athlon XP 2.600 Barton with 512 mb RAM (Dual Channel) and a ATI Radeon 9600 128 mb, but for some reason my Ubuntu 5,10 runs at a low speed.  
I downloaded the latest ATI drivers but it is still slow. I also got the linux kernel for k7 (i was using for i386), but it is still slow. Since I'm new in Ubuntu comunity, I ask someone for help on optimizing my OS. :confused:

---

### Post by doclivingston on 2005-10-11
What exactly is slow? Starting up, loading programs, using programs, moving windows around?

---

### Post by viniciustp on 2005-10-11
Thanks for the fast reply!
It's slow when i move windows around. It shows, for example a trail when i move them. Running programs is also slow, even lightweight ones, such as Firefox.
Also, i didn't create a swap partitin, cause i tought 512mb RAM would be enought for running the system.
Thanks again!

---

### Post by aysiu on 2005-10-11
[QUOTE=viniciustp]Running programs is also slow, even lightweight ones, such as Firefox.[/QUOTE] Firefox is a lightweight program?

---

### Post by HermanAB on 2005-10-11
With only 512MB RAM, you need a swap partition of at least 1GB, preferably 2GB.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by viniciustp on 2005-10-11
[QUOTE=aysiu]Firefox is a lightweight program?[/QUOTE]

I tought it was. :???:  But thanks for help.

---

### Post by viniciustp on 2005-10-11
[QUOTE=HermanAB]With only 512MB RAM, you need a swap partition of at least 1GB, preferably 2GB.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)[/QUOTE]

Thanks! I'll try it now!!!

---

### Post by aysiu on 2005-10-12
[QUOTE=HermanAB]With only 512MB RAM, you need a swap partition of at least 1GB, preferably 2GB.[/QUOTE] That might help, but I have 512 MB of RAM, and I almost never dip into swap. Something else is wrong. When I type ```
top
``` into a terminal, this is my output ```
Tasks:  81 total,   1 running,  78 sleeping,   0 stopped,   2 zombie
Cpu(s):  8.5% us,  0.5% sy,  0.2% ni, 89.9% id,  0.6% wa,  0.2% hi,  0.0% si
Mem:    451852k total,   429124k used,    22728k free,    24516k buffers
Swap:  1060248k total,        0k used,  1060248k free,   236148k cached

``` You'll notice, with Firefox, Thunderbird, and a terminal running, I'm using 0 swap, and I still have 22,728k free in my normal memory.

viniciustp, when you type ```
top
``` into a terminal, what pops up?

---

### Post by viniciustp on 2005-10-12
[QUOTE=aysiu]That might help, but I have 512 MB of RAM, and I almost never dip into swap. Something else is wrong. When I type ```
top
``` into a terminal, this is my output ```
Tasks:  81 total,   1 running,  78 sleeping,   0 stopped,   2 zombie
Cpu(s):  8.5% us,  0.5% sy,  0.2% ni, 89.9% id,  0.6% wa,  0.2% hi,  0.0% si
Mem:    451852k total,   429124k used,    22728k free,    24516k buffers
Swap:  1060248k total,        0k used,  1060248k free,   236148k cached

``` You'll notice, with Firefox, Thunderbird, and a terminal running, I'm using 0 swap, and I still have 22,728k free in my normal memory.

viniciustp, when you type ```
top
``` into a terminal, what pops up?[/QUOTE]

That's what pops up:

Mem:    516320k total,   407724k used,   108596k free,    43060k buffers
Swap:        0k total,        0k used,        0k free,   172268k cached

Over 100mb free. Any ideia what it could be?

---

### Post by aysiu on 2005-10-12
[QUOTE=viniciustp]That's what pops up:

Mem:    516320k total,   407724k used,   108596k free,    43060k buffers
Swap:        0k total,        0k used,        0k free,   172268k cached

Over 100mb free. Any ideia what it could be?[/QUOTE] That is strange. With the same amount of memory, you have more free than I do. Hm. I did have a dragging windows "stuttering" problem in Gnome once, but it was because of a "heavy" theme. The Firefox and other applications being slow, though, I don't know about... There are tips to make Firefox faster. I'm assuming you don't mean the actual browsing is slow but the responsiveness or the loading up of the program.

---

### Post by doclivingston on 2005-10-12
[QUOTE=aysiu]```
Tasks:  81 total,   1 running,  78 sleeping,   0 stopped,   2 zombie
Cpu(s):  8.5% us,  0.5% sy,  0.2% ni, 89.9% id,  0.6% wa,  0.2% hi,  0.0% si
Mem:    451852k total,   429124k used,    22728k free,    24516k buffers
Swap:  1060248k total,        0k used,  1060248k free,   236148k cached

``` You'll notice, with Firefox, Thunderbird, and a terminal running, I'm using 0 swap, and I still have 22,728k free in my normal memory.[/QUOTE]

You also have over 230Mb cached, which is memory that the kernel uses to keep copies of things on disk, because it isn't being used for anything else. So in actualy fact less than half your ram is actually used by applications.

---

### Post by aysiu on 2005-10-12
[QUOTE=doclivingston]You also have over 230Mb cached, which is memory that the kernel uses to keep copies of things on disk, because it isn't being used for anything else. So in actualy fact less than half your ram is actually used by applications.[/QUOTE] But viniciustp has even more cached, so that doesn't solve the mystery. Thanks for explaining about the cached memory, though.

---

