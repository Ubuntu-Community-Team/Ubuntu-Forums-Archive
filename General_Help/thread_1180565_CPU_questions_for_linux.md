---
title: "CPU questions for linux"
date: 2009-06-07
forum: General Help
---

### Post by noob707 on 2009-06-07
Well, i have some CPU questions for ubuntu.

-what is a good linux program to overclock my CPU(Instead of going to the BIOS)

-does the latest kernel 2.6.x support the speedstep technology of intel processors

-I like my games:p

so when i play certain games(with wine), i would like to make Core0 for ubuntu and the other cores devoted to just the game. Can i do this or is there a program where i can manage which core certain apps can have. For example:
Whenever i start WoW with Wine, i would to make Core0 for ubuntu, Core1 and Core2 for WoW and Core3 for any program that wants to access it(like firefox). Is there a program where i can manage like profiles on certain Core options.

Thanks,
Noob707

---

### Post by colau on 2009-06-07
> **noob707 said:**
> Well, i have some CPU questions for ubuntu.

-what is a good linux program to overclock my CPU(Instead of going to the BIOS)

-does the latest kernel 2.6.x support the speedstep technology of intel processors

-I like my games:p

so when i play certain games(with wine), i would like to make Core0 for ubuntu and the other cores devoted to just the game. Can i do this or is there a program where i can manage which core certain apps can have. For example:
Whenever i start WoW with Wine, i would to make Core0 for ubuntu, Core1 and Core2 for WoW and Core3 for any program that wants to access it(like firefox). Is there a program where i can manage like profiles on certain Core options.

Thanks,
Noob707
:p
```

cat /proc/cpuinfo

```

---

### Post by hansdown on 2009-06-07
Hi noob707.

If you search synaptic, you can install a number of things.

cpudyn, cpufreq,cpufrequtils, cpulimit.

---

### Post by DeMus on 2009-06-07
> **hansdown said:**
> Hi noob707.

If you search synaptic, you can install a number of things.

cpudyn, cpufreq,cpufrequtils, cpulimit.

The mentioned programs don't do what the OP wants: that is to control which cpu core does which task.

---

### Post by rcayea on 2009-06-07
Because you always want a benchmark...

Also, to add to the previous post, CPU Burn-in by Michal Mienik is the ultimate stability testing tool for overclockers.

---

### Post by noob707 on 2009-06-07
thanks for the posts but my major concern is to control which cores control what and do what.

---

### Post by ushimitsudoki on 2009-06-07
> **noob707 said:**
> thanks for the posts but my major concern is to control which cores control what and do what.

Yes, [bind]("http://linux.die.net/man/2/bind").

[Here]("http://www.linuxjournal.com/article/6799") is a fairly detailed article on setting processor affinity in Linux - maybe that will get you going?

Good luck!

---

### Post by noob707 on 2009-06-07
thanks a lot ushim. That was exactly i was looking for.

---

