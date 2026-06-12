---
title: "Compiz are consuming more than 100% of my cpu"
date: 2017-06-22
forum: Desktop Environments
---

### Post by yurilion123 on 2017-06-22
Compiz are consuming more than 100% of my cpu, without any window opened. That's starts without any changes on the configurations or effects of Compiz. My notebook have a core i3 - 4x 2.20GHz, Unity 7 and ubuntu 16.04. I'm newbie at the Linux world and i don't know what can i do to fix it.

---

### Post by kyrithis on 2017-06-22
Just to confirm, this is a fresh installation of Ubuntu 16.04? We'll try to fix the problem with smaller measures, but a system upgrade may fix this issue. Let's hope it doesn't come to that, 16.04 is the most recent LTS version I believe.

---

### Post by Autodave on 2017-06-22
Me personally, I would remove Compiz and see what I had and go from there.

---

### Post by deadflowr on 2017-06-22
Typcailly compiz eating is caused by a borked gpu driver (or no driver at all)

To see what the current driver is and the card you have, open a terminal and run:
```
lspci -vnn | grep VGA -A 10
```
shows.

Also you can see what is what with 
```
glxinfo
```
but that command is part of a package that needs to be installed,
to install the package for that command run
```
sudo apt-get install mesa-utils
```

post back the results if you can, please.

---

### Post by yurilion123 on 2017-06-24
Thanks for the help. I think that i've installed the 16.04 1 year ago, but i update it whenever i can. I'm using a Sandybridge and already have the mesa-utils. Now i'm using the metacity, but with him i'm having problems with execute some programs. WIthout the compiz, evertything are running ok, except some programs. Sorry for my english, i'm learning yet.

DeadFlowr, here the result of the command: 
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])	Subsystem: Hewlett-Packard Company 2nd Generation Core Processor Family Integrated Graphics Controller [103c:1854]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at c2000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

---

