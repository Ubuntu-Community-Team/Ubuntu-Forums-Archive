---
title: "slows down and ultimatly freezes"
date: 2008-08-22
forum: Desktop Environments
---

### Post by Tjaalie on 2008-08-22
Dear Threadreader,

I have been running Debian for quite a while, but lately I became intrested in Ubuntu. And so far it gives me a more professional impression then Debian. But there is one really big problem that gets me from switching over for good. Say once every 1 or 2 hours Ubuntu begins to slow down, this takes like 5 to 10 minutes and then it freezes, I can't click anything and the keyboard is not responding (the keyboards lights neither). But the cursor can still be moved. Ctrl-Alt-F1 doesn't work anymore and I can't really do anything. I experienced this before and after I installed the non-free NVidia drivers, so this can't be a problem (or there must be a bug in both). If any of you guys needs more info please ask. I tried to view the logs with gnome system log viewer but I don't know witch logs to search and for what to search. So I'm kinda out of idea's. But maby the fact that I have no problems on Debian can help? Because I tough the where quite similar the problem must be in one of its differences.

Thanks in advance,

Tjaalie

---

### Post by OnlyWhisky on 2008-08-22
I think something is wrong with your Advanced Control Power Managment Interface (ACPI). If you do hibernation or suspend your OS to ram than it should be the reason. Else it could be wrong information about CPU temperature or something. (just guess)

I have seen same behavior six or sevent times by myself.

---

### Post by Tjaalie on 2008-08-22
I get it once every 1 or 2 hours. Is there a way to bypass this? Even if this totally dangerous. Debian didn't do this, does it use a other way to handle those things? Can I somehow install the Debian programs who do these things?

---

### Post by puppywhacker on 2008-08-22
Hi,

If you open a terminal (or two) and run "top" on it you get the process statistics sorted on CPU usage. press "M" will sort the process on memory usage.

What you are looking for is the command that is eating up your system, both CPU and Memory. As an example, below are my values, try to find a guilty process, otherwise it might be an ACPI problem or hardware failure

(my example top, press "q" for quit, or CTRL-C)

Cpu(s):  2.4%us,  0.7%sy,  0.0%ni, 96.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3796368k total,  3194236k used,   602132k free,   111640k buffers
Swap:  2257092k total,        0k used,  2257092k free,  2215288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6312 root      20   0  589m 148m  25m S    3  4.0  20:34.62 Xorg 


1 ... 96.9%id means my processor's aren't doing much
2 ... I still have "602132k free" memory
3 ... I use "0k used" for memory swap
4 ... The one doing the most work 3% CPU and 4% memory is in my case process 6312 which is XOrg

---

### Post by tangibleorange on 2008-08-22
> **puppywhacker said:**
> Hi,

If you open a terminal (or two) and run "top" on it you get the process statistics sorted on CPU usage. press "M" will sort the process on memory usage.

What you are looking for is the command that is eating up your system, both CPU and Memory. As an example, below are my values, try to find a guilty process, otherwise it might be an ACPI problem or hardware failure

(my example top, press "q" for quit, or CTRL-C)

Cpu(s):  2.4%us,  0.7%sy,  0.0%ni, 96.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3796368k total,  3194236k used,   602132k free,   111640k buffers
Swap:  2257092k total,        0k used,  2257092k free,  2215288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6312 root      20   0  589m 148m  25m S    3  4.0  20:34.62 Xorg 


1 ... 96.9%id means my processor's aren't doing much
2 ... I still have "602132k free" memory
3 ... I use "0k used"
4 ... The one doing the most work 3% CPU and 4% memory is in my case process 6312 which is XOrg

yes do this when you first boot. leave it in the background. then when it stalls, you can check the contents of this output (i understand you still have mouse input). it might reveal what is causing the problem.

---

### Post by Tjaalie on 2008-08-22
Mouse input is not the right word. I can move the cursor but clicking doesn't do anything and when I hover buttons or text boxes (or any other GUI item) it doesn't respond in any way.

---

### Post by OnlyWhisky on 2008-08-22
Try add acpi=off to your kernel boot option and test if slowness would happen. But notice that all your usb devices would not work. 

Also try to open pc case etc. for me problem was with too hot mainboard chipset.

---

### Post by tangibleorange on 2008-08-22
yeah add the boot options:

```
apm=off acpi=off noapic nolapic
```

---

