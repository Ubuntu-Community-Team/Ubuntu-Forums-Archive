---
title: "Xorg hogging CPU when Nicotine renders"
date: 2005-12-20
forum: Desktop Environments
---

### Post by albamuth on 2005-12-20
On a  1.8 Ghz AMD with 512Mb RAM

```
top - 10:08:56 up 1 day,  9:22,  4 users,  load average: 4.50, 4.39, 3.99
Tasks:  86 total,   2 running,  84 sleeping,   0 stopped,   0 zombie
Cpu(s): 90.1% us,  5.3% sy,  3.3% ni,  0.0% id,  0.0% wa,  0.3% hi,  1.0% si
Mem:    516492k total,   500376k used,    16116k free,    58988k buffers
Swap:  1071968k total,    12476k used,  1059492k free,   117980k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6971 root      25   0  213m  69m  17m R 87.9 13.8 632:05.95 Xorg

```

:~$ xdriinfo
xdriinfo: symbol lookup error: xdriinfo: undefined symbol: glXGetProcAddress

It doesn't happen after boot-up, but after I leave for a while (screensaver disabled), say overnight, I come back and both top and the gnome-system monitor show maxing out the CPU, and this is before I evene start moving windows around.

I noticed that nicotine, which is python-based, *I believe*, takes a long time to render its windows after I leave it running for a while, even though that process is basically sleeping. In fact, I'm pretty sure this has to do with Nicotine.

Questions: is it Nicotine that makes Xorg chew up CPU cycles? is there a better soulseek client? does python just suck or what?

---

