---
title: "powernowd, lower limit less than 600"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Ralle on 2006-08-22
Hello guys!
I installed ubuntu and I really like it.. the only things that bother me is that I cant use OneNote and that the minimum cpu limit is at 600 mhz.. how do I lower it?
I said powernowd -l 10 but it didnt work

---

### Post by Ramses de Norre on 2006-08-22
What is onenote, and if it's a program for linux/ubuntu: what's the problem/error?

And for the cpu frequency: cpu's only support a number of frequencies, and 600MHz seems the lowest one yours supports.. nothing to do about. (and you can be glad with that value I think, mine can't go lower than 1GHz)

---

### Post by Ralle on 2006-08-23
well isnt there a way to set it?
I mean.. I am not able to set it to anything.. it doesnt recieve what I tell it

---

### Post by RAOF on 2006-08-23
> **Ralle said:**
> well isnt there a way to set it?
I mean.. I am not able to set it to anything.. it doesnt recieve what I tell it

No.  The processor only has a fixed number of speed-throttling states, and these are hardwired.  The lowest state for you is obviously 600MHz.  For me, it's 1GHz.  There's no way of telling the processor "go below your minimum speed".

If you check out the man page, the "-l 10" switch is for setting when powernowd should drop the CPU frequency.  With "-l 10", powernowd will only decrease the frequency when the CPU utilisation drops below 10%.

---

### Post by Bharath on 2006-09-04
Hi,

Check out [http://memoranda.sourceforge.net/](http://memoranda.sourceforge.net/) for Onenote replacement. Memoranda has more than 50% of the functionalities of OneNote.

Bharath

---

### Post by nelio2k on 2008-02-13
I was wondering the same thing.

I have a Thinkpad X41 with a Pentium M 758 of 1.5 Ghz. The lowest it goes is 600 Mhz.

However, in Windows, when I go under System Properties in battery saving mode, it shows that the processor is running at 248 Mhz or something like that.

So how does this work? How could windows manage to lower the speed to less than 600 Mhz when linux can't? Is Windows doing undervolting? Moreso, I can tell the difference because I get an extra half an hour of battery life in Windows than I do in Ubuntu. So, I suspect that it is the processor speed that makes a difference?

If anyone has an answer it'd be awesome. Thanks in advance.

---

