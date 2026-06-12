---
title: "How to luanch a program/process on a fixed CPU?"
date: 2008-12-30
forum: General Help
---

### Post by icedfusion on 2008-12-30
Hi,

I use my machine for alot of computationally intensive stuff and have found that at times, I have a conflict of CPU usage on my quad core.

I know there is an inbuilt scheduler for processes but I would like to fix certain programs to certain cores.

Example:
Core 0: General desktop usage
Core 1: NZB/Newgroup downloading/processing
Core 2: Video Playback.
Core 3: General desktop usage.

What I am really asking is if I can execute certain programs like mplayer/lottanzb/hellanzb to run on certain cores?

Thanks

ice.

---

### Post by dcstar on 2008-12-30
> **icedfusion said:**
> Hi,

I use my machine for alot of computationally intensive stuff and have found that at times, I have a conflict of CPU usage on my quad core.

I know there is an inbuilt scheduler for processes but I would like to fix certain programs to certain cores.

Example:
Core 0: General desktop usage
Core 1: NZB/Newgroup downloading/processing
Core 2: Video Playback.
Core 3: General desktop usage.

What I am really asking is if I can execute certain programs like mplayer/lottanzb/hellanzb to run on certain cores?


AFAIK one of the reasons that processes are automatically switched between cores is to ensure that the heat load is spread evenly between them so any chance of localised heat differential is reduced.

If you run processes on specific cores you run the risk of "hot spots" on the CPU die - or worse, a core continually heating up and cooling down while nearby there is a major temperature difference - and I'm fairly sure that isn't a good thing.

---

### Post by sdennie on 2008-12-30
You can use taskset to set CPU affinity for a process.  However, you may be able to alleviate your problems by running them with nice.  Starting your long running number crunching software with "nice" in front of it will make your machine prefer your interactive tasks.  One caveat with this approach is that it used to be (and probably still is) the case that a niced process doesn't get considered by the CPU scaling governor when deciding what frequency to run at.  If that's a problem for you, you may need to manually set the CPU governor to performance:

```

sudo cpufreq-selector -g performance

```

---

