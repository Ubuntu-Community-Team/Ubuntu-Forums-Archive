---
title: "Why is my installation swapping so much?"
date: 2011-05-19
forum: Desktop Environments
---

### Post by LonelyStar on 2011-05-19
Hi,

I have installed xubuntu. I have a total of 12034MB of main Memory of which ~1000MB are normally used.

When I leave the computer and come back, it is swapping a lot. Whenver I display a window (firefox i.E.) that I have not displayed yet since I left the computer alone, I can here the HD working, and the system monitor shows me how more memory is used and less swap space.

But there is absolutely no need for it. I have at least 10000MB of free Memory at all the time!

Can I somehow tell my xubuntu installation to stop swapping unless there is really little main memory left (lets say less than 2000MB)?

My kernel version is 2.6.35-29-generic because I have trouble with the raw1394 module in the newest version.

Thanks!
Nathan

---

### Post by prshah on 2011-05-19
> **LonelyStar said:**
> 
Can I somehow tell my xubuntu installation to stop swapping unless there is really little main memory left (lets say less than 2000MB)?

You can adjust the "swappiness": Open a terminal (Applications-Accessories-Terminal) and give the command
```
sudo sysctl -w vm.swappiness=20
```

You can use a lower value if you like, but avoid "0". The lower the value, the lesser chances of swap being used. The default for Ubuntu is 60.

Then use the machine for a while and see if it's OK. If you feel it's OK, to make the change permanent:

Edit the file /etc/sysctl.conf ```
gksudo gedit /etc/sysctl.conf
``` and add a single line to the end of the file (don't change any other contents)```
vm.swappiness=20
``` Then save and exit. Now, the setting will persist across reboots.

---

### Post by LonelyStar on 2011-06-06
Hey,

OK, I tried a bit around (and gave it time). I have not set swappiness = 1 and it is still sawpping when it is completely unnecessary, but only if the computer is idle.

Is there something else I could do?

Thanks!
Nathan

---

### Post by mcduck on 2011-06-06
> **LonelyStar said:**
> Hey,

OK, I tried a bit around (and gave it time). I have not set swappiness = 1 and it is still sawpping when it is completely unnecessary, but only if the computer is idle.

Is there something else I could do?

Thanks!
Nathan

Are you absolutely sure it's swapping, and not doing some other task like indexing the filesystem or rotating log files etc. It's just that swapping when idle wouldn't make any sense, while task like those are intended to run when the user is idle and the system has some "free time".

What does *free -m* say? And *top* output of course. And are you using any kind of automatic backup solution or any other program one might expect to run in the background and access disc?

(the swappiness setting probably doesn't help here, it's not a direct control over swap usage, only one of the values used to determine when to use swap and when to drop cached data instead. (even when the swappiness is set to 0 the kernel will swap if it needs to, and even if you set swappiness to 100 the system will not all the time swap data instead of dropping cached data.)

---

### Post by LonelyStar on 2011-06-06
Hey,

I am not using any backup program or anything indexing files but what the default xubuntu installation.

The output of free -m
```

free -m
             total       used       free     shared    buffers     cached
Mem:         12034       3054       8979          0         77        790
-/+ buffers/cache:       2187       9846
Swap:        15999        621      15378

```

So right now, I have 621MB swap used. OK, I do not feel any lagishness.
But after the computer was idle for some time, swap goes up to 1500MB (I am watching it using xfces system monitor panel item) and everything is very unresponsive at first.

When I activate firefox, the HD starts to work and the window is not shown correctly for about half a minute. During this progress, I can watch the swap freed in the system monitor panel item.

Any other/additional advice?

Thanks!
nathan

---

