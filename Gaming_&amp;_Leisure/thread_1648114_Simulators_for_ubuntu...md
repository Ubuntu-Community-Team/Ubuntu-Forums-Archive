---
title: "Simulators for ubuntu.."
date: 2010-12-18
forum: Gaming &amp; Leisure
---

### Post by 21stCenturyBreakdown on 2010-12-18
Hey! im like new to the forum, so im not sure whether this is the right place :L
so anywho..can anyone list good simulators for ubuntu eg: flight sims etc.. :)

Thanks

---

### Post by I'mGeorge on 2010-12-18
> **21stCenturyBreakdown said:**
> Hey! im like new to the forum, so im not sure whether this is the right place :L
so anywho..can anyone list good simulators for ubuntu eg: flight sims etc.. :)

Thanks

-[flight gear]("http://www.flightgear.org/") as a flight sim

- [danger from the deep]("http://dangerdeep.sourceforge.net/") as a submarine sim, currently in alpha state, being a work in progress but it's playable and really entertaining.

-[torcs]("http://torcs.sourceforge.net/"), trigger, vdrift,speed dreams, dakar 2010 as racing simulators

- [vega strike]("http://vegastrike.sourceforge.net/getfiles/") and vendetta online as sci-fi flight sims

- using wine you can run IL2-Sturmovik without a problem also, as a WW2 combat flight simulator.

- [mania drive]("http://maniadrive.raydium.org/index.php?downloads=yes") as an entertaining car stunts simulator

- [frets on fire (FOFIX)]("http://fretsonfire.sourceforge.net/") as a guitar simulator. You can make a guitar out of your keyboard.

- [True Combat Elite]("http://www.truecombatelite.com/")as one of the most realistic online FPS I have ever encountered

---

### Post by 21stCenturyBreakdown on 2010-12-18
how would i install a tar.gz file O.o

---

### Post by fatal_ERROR777 on 2010-12-18
.tar.bz is a Linux tarball. This is an analog for windows's .RAR or .ZIP format of archive. You just need to unpack it somewhere ( I prefer /home/your_username/Documents/). After, find a makefile (the file that will compile & install the software) and run it. You better it in terminal to see error messages.


```
dima@dima-laptop:~$ cd /home/dima/Documents/mars_linux_0.6.1_alpha/ 
dima@dima-laptop:~/Documents/mars_linux_0.6.1_alpha$ /home/dima/Documents/mars_linux_0.6.1_alpha/M.A.R.S.
./main32: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory
```

This is an example of installing these programs. Unfortunately, the developers of this game, [M.A.R.S.]("http://mars-game.sourceforge.net/") have written the libraries incorrectly. The makefile for my game is M.A.R.S. , but you might have a different file. But don't worry, your .tar.bz should work 

**P.S.** "cd" is change directory command. And, a little bit of explaination:
cd /home/dima/documents/mars_linux_0.6.1_alpha/  - I have changed my directory to the uncompressed folder. 
/home/dima/Documents/mars_linux_0.6.1_alpha/M.A.R.S. - I have tried to launch the makefile. 

**I'mGeorge**, you are right! Firstly, search your game in synaptic, synaptic will all of the job for you! Go to System -> Administrative ->  Synaptic package manager and search for your game that you wish to install


Fatal_Error

---

### Post by I'mGeorge on 2010-12-18
> **21stCenturyBreakdown said:**
> how would i install a tar.gz file O.o

Before trying to install from source,the usual case of tar.gz archives, search if you don't have the game in your repositories with synaptic. Some games also came archived as tar.gz even if they are precompiled and you already have some available executables. 

Tell me what are you trying to install so I could assist you forward.

---

### Post by glopal on 2011-01-24
I'm making a remake of the classic physics simulator "Ski Stunt Simulator." 

Here's a gameplay video, please keep in mind it's still under development.

**Mars Stunt Simulator Progress Video #2**
[http://www.youtube.com/watch?v=tE1Fo1sJx2I]("http://www.youtube.com/watch?v=tE1Fo1sJx2I")

I'm posting this because of it's extreme relevance to this thread. I use Ubuntu both at home and at work. The simulator is made in Java and is fully cross platform.

I'm sorry for bringing an old thread back from the dead, and also technically advertising. [-X My bad. XD

---

### Post by mips on 2011-01-24
[www.x-plane.com](www.x-plane.com)

---

### Post by CivilizationII on 2012-02-20
Undoubtly FlightGear (aircraft) and Torcs (car). X-Plane (aircraft) if you are willing to pay for the simulator.

---

