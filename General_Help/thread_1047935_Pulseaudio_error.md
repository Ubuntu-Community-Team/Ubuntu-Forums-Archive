---
title: "Pulseaudio error"
date: 2009-01-22
forum: General Help
---

### Post by Bios Element on 2009-01-22
So I'm not entirely sure what happened but pulseaudio will not start. Here's the terminal dump. Earlier today I was trying to get Smokin Guns working and made a sym link or something like that. But I don't have the command and I'm kinda unsure of what to do. Anyone have any ideas?

```
william@william-desktop:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: module-hal-detect.c: Failed to parse module arguments
E: module.c: Failed to load  module "module-hal-detect" (argument: "tsched=0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

```

EDIT: I found a few commands I ran trying to get it to work. (Yes, I'm an idiot. My bad for randomly running commands. >.> I should know better...)
```

sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0/home/william/SmokinGuns/smokinguns.x86
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0

```

---

### Post by Bios Element on 2009-01-22
Solved. Purged and Re-installed Pulse.

---

