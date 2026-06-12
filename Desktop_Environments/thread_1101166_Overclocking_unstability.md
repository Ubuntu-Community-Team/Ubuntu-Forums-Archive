---
title: "Overclocking unstability"
date: 2009-03-20
forum: Desktop Environments
---

### Post by TurpoNieminen on 2009-03-20
I am wondering is ubuntu really this sensitive to overclocking or is there something else going on?

I have a E2160 processor that is rock solid and passing all stress/CPUburn tests running 1,8@3,3Ghz in windows. 
In Ubuntu, system is unstable even running 1,8@2,7Ghz(lowest that i tried) and doing simple not so CPU intensive tasks.

I am just wondering... When i installed Ubuntu i was running at standard 1,8Ghz. Does Ubuntu somehow "remember" that setting and mess things up when i try to overclock?
Should i try to install Ubuntu again running 3,3Ghz?

---

### Post by mcduck on 2009-03-20
Linux, in general, is more sensitive about correctly working hardware, and tends to stop working if things are not going as they should. Windows instead continues working, although possibly causing the programs you run to produce wrong results and sometimes other kinds of data corruption as well.

It can of course be argued which one is the best way to go, but for OS used on servers and supercomputers it makes sense to not risk correctness of the users data.

So, it could just be that your computer isn't absolutely stable at that speed, Windows just lets you continue anyway (at your own risk).

---

### Post by TurpoNieminen on 2009-03-20
Thanks, i guess i have to lower my clock ratios to find stable speed then. However i find this little bit odd, because i can't produce cpu errors in windows even using any CPU burning/testing software.

I use windows for games anyway, so i don't need to run Linux at max Ghz setting.

---

### Post by mcduck on 2009-03-20
Try running something like Prime95 for long times, at least overnight. Shorter tests don't give reliable info about system's stability. If the system survives that then it *should* be stable in Linux as well at the same speed.

Of course it *is* possible that the drivers you are using in Linux for your hardware create enough difference to make the system less stable overclocked. But I'd make sure that it's absolutely stable at those clock speeds in Windows before starting to troubleshoot Linux.

---

