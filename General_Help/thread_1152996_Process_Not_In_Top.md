---
title: "Process Not In Top"
date: 2009-05-08
forum: General Help
---

### Post by mgarl10024 on 2009-05-08
Hi,

This is probably an easy question for someone experienced. ;-)

I've got an application (fcrackzip) which it using the CPU flatout.
Now, I'm happy that the CPU is being used - the program is doing things, the cpu has ramped up in response to the load from 1ghz to the full 2.3ghz, the power usage has gone up, more heat is being produced, etc. etc.  I am confident that this program is running.

However, what I don't understand is that top (and the Ubuntu System Monitor) both report a low total CPU usage (a few %)!  I would also expect the process to be using over 90% of the CPU, but it's using hardly anything.  The only difference there is that the load factors (which I still don't have a grip on!) have gone up.
Even ps-Af doesn't report any process with a huge CPU time.

As I ran the process, and it's clearly running flat out, I'm just confused as to why it doesn't show up in the system monitoring stuff.  I did read that fcrackzip was written in assembler, so maybe that doesn't show?  Clutching at straws...

Thanks in advance

MG

---

### Post by mgarl10024 on 2009-05-11
No-one?  :(

---

### Post by mgarl10024 on 2009-12-30
Hi,

I've never managed to resolve this one, even though I've been using Ubuntu for most of this year.

The situation has got worse for me since upgrading from Kernel 2.6.27-7-generic to 2.6.31-16-generic, because with 2.6.27 the machine was an excellent file server and ran fcrackzip in the background, but with 2.6.31 frackzip seems to be taking precedence meaning that the machine becomes a lousy file server with awful file transfer rates!
However, how can I set the frackzip processes to a lower priority or a higher nice value, if I can't find them?

I've just kicked off fcrackzip again, and you can see below that the cpu is flat out (0.0%id), but then look at the list of processes and there is nothing there that is using it?  frackzip is only using a tiny amount.

The only thing I can think of is that fcrackzip is spawning millions of tiny little short lived processes that don't show up in top - how would I find these?

```

top - 14:34:32 up 15:31,  2 users,  load average: 0.53, 0.12, 0.04
Tasks: 189 total,   4 running, 185 sleeping,   0 stopped,   0 zombie
Cpu(s): 85.8%us, 13.9%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   3928580k total,  3337476k used,   591104k free,   505072k buffers
Swap:  3903672k total,        0k used,  3903672k free,  1815484k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 4211 mark      20   0  212m  15m  10m S  2.6  0.4   0:00.47 gnome-terminal                                                  
 2779 mark      20   0 55560  14m 3956 S  1.3  0.4   1:23.41 Xvnc                                                            
 4232 mark      20   0  3964  608  500 R  0.7  0.0   0:00.04 fcrackzip                                                       
 5087 mark      20   0  7408 1712  624 R  0.7  0.0   0:00.02 unzip                                                           
    1 root      20   0 19568 1896 1176 S  0.0  0.0   0:00.51 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 
.....
.....
.....

```

All help appreciated!

Thanks,

MG

---

### Post by john newbuntu on 2009-12-30
Well the top command shows 0% idle.  so your cpu is in full use.  Perhaps your sort order is wrong.  I do not know how to scroll up or down in top.  I know that the top on unix systems had the feature to scroll.  Anyway, if you want to renice a process (if you know the pid), then type r when top is running.
I personally use htop.  Just install it using the usual apt-get install command. It allows scrolling.

---

