---
title: "Minecraft in full-screen keeps bringing down my Ubuntu desktop!"
date: 2010-12-22
forum: Gaming &amp; Leisure
---

### Post by mathuin on 2010-12-22
I love playing Minecraft in full-screen except when it brings down my Ubuntu desktop.

I am running Ubuntu 10.10 64bit desktop which I update religiously.   I have 4G of onboard RAM and a 3.00GHz quad-core Q6850 processor.  My  video card is a GeForce 8800GT.  I am currently running driver version  260.19.29.Here is my uname: 

```
Linux belle 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux 
```What I expect to happen is to keep on playing happily.  What happens within an hour of starting the game is the screen goes black and the computer's fans go wild.  When I ssh into my desktop, I see the java process via ps and it looks like this (please excuse the hand-typed information, cut and paste is not working on my other system):

```
jmt 11304 95.6 14.5 1964044 588460 ? Sl 11:11 21:07 /usr/lib/jvm/java-6-sun-1.6.0.22/bin/java -jar /home/jmt/Downloads/Minecraft.jar
```When I try to kill the process, nothing good happens.  After kill, kill -1, and kill -9, ps looks like this:

```
jmt 11304 89.6 0.0 0 0 ? Zl 11:11 21:07 [java] <defunct>
```The desktop never returns.  Eventually the ssh session stops responding.  The only recovery is to reboot the entire system.

This happens in single-player mode as well as multi-player mode.  This happens when I use Sun Java 6 and also when I use OpenJDK Java 6.  I even tried backing my video drivers down from "version current" to "version 173" with no difference.  I have played for two or three hours at a time in windowed mode and have never seen any trouble, so I think it's something about windowed mode.

When I recreate this problem by ssh'ing into the desktop and starting Minecraft, nothing is output by Minecraft when the screen goes black -- no log entries, no nothing.

For now, I'm using a workaround of "don't use full-screen and get over it when it crashes" but that totally stinks.  Help!  My happy fun time during break rides on you guys. :-)  

Thanks in advance!

Jack.

---

### Post by mathuin on 2010-12-22
I checked the Xorg.0.log.old and found this very interesting tidbit:

```

[ 12634.207] (WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0xdfff2fff, 0x00003d68)
[ 12641.207] (WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0xdfff2fff, 0x00003d68)
[ 12641.208] 
Backtrace:

```There's no actual backtrace, but it does look like a bug in the NVidia driver.  How do I report this?

Jack.

---

