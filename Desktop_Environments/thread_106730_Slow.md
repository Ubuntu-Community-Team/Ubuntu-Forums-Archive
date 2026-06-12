---
title: "Slow????"
date: 2005-12-21
forum: Desktop Environments
---

### Post by Yv12345vY on 2005-12-21
Why is Ubuntu so slow?

I'm running an Alienware Sentia 1.6ghz 1gb ram 60gb 7200rpm hdd Centrino based machine.  I installed Ubuntu last night and while I love it :p  I am very disappointed with the performance. :( 

For some reason, the system always reports a 100% CPU load and the hard drive keeps spinning at all times.  Yet, the system monitor reports itself as being the heaviest CPU user.  Any ideas what may be wrong? :confused: 

By slow, I mean that the system takes at least 5 minutes to show me the login screen and opening applications is painful.  Even loading pages in Firefox takes much longer than it should.  Help is appreciated.

---

### Post by stalefries on 2005-12-21
Something is obviously mal-configured. I'm sorry, but I can't think of anything off the top of my head. Can you give the output of the command "top"?

---

### Post by arnieboy on 2005-12-21
[QUOTE=Yv12345vY]Why is Ubuntu so slow?

I'm running an Alienware Sentia 1.6ghz 1gb ram 60gb 7200rpm hdd Centrino based machine.  I installed Ubuntu last night and while I love it :p  I am very disappointed with the performance. :( 

For some reason, the system always reports a 100% CPU load and the hard drive keeps spinning at all times.  Yet, the system monitor reports itself as being the heaviest CPU user.  Any ideas what may be wrong? :confused: 

By slow, I mean that the system takes at least 5 minutes to show me the login screen and opening applications is painful.  Even loading pages in Firefox takes much longer than it should.  Help is appreciated.[/QUOTE]
u need to do two things:
1) install the appropriate drivers for your video card 
2) upgrade the kernel to 686 from 386.

---

### Post by Yv12345vY on 2005-12-21
arnieboy, how do I do these updates?  I'm not sure if I should just download the kernel sources and install or if I there is a way to do it via the UI.

---

### Post by Yv12345vY on 2005-12-21
[QUOTE=stalefries]Something is obviously mal-configured. I'm sorry, but I can't think of anything off the top of my head. Can you give the output of the command "top"?[/QUOTE]

Top, by CPU usage, processes are top, dbus-daemon, acpid, power.sh, hald, kacpid, on_ac_power.  I saw power management come up as an issue in other posts.  I'm going to play around with that to see if I can get any better performance.

---

### Post by Yv12345vY on 2005-12-22
[QUOTE=arnieboy]u need to do two things:
1) install the appropriate drivers for your video card 
2) upgrade the kernel to 686 from 386.[/QUOTE]

I figured out how to do #2.  I think it is slower now than before. 

If I kill all the power management related processes the CPU load normalizes and the hdd doesn't spin all that much.  Any ideas what I can do about that?  Startup is still painfully slow however.

How do I know which drivers I have for my video card?  How do I update those?

---

### Post by arnieboy on 2005-12-22
[QUOTE=Yv12345vY]I figured out how to do #2.  I think it is slower now than before. 

If I kill all the power management related processes the CPU load normalizes and the hdd doesn't spin all that much.  Any ideas what I can do about that?  Startup is still painfully slow however.

How do I know which drivers I have for my video card?  How do I update those?[/QUOTE]
which video card do u have? do u know that?

---

### Post by Yv12345vY on 2005-12-22
[QUOTE=arnieboy]which video card do u have? do u know that?[/QUOTE]


It's the Intel 82852/82855 GM/GME series.

---

### Post by Benchrest on 2005-12-23
I am not hijacking this thread but I have simaler problem. But not every boot. Try rebooting and see if it happens every boot. It will show 100% cpu but the only heavy use application is the system monitor just like yours. It will show about 45%. Where is the rest used? I need more research before opening my own problem, but **where do you find the power management setting you mentioned**? By the way, if I reboot the system is fine. I only notice this on my laptop that has no battery installed and is running on AC.

---

### Post by fordfan753 on 2005-12-23
I've seen problems on lots of machines where the update-notifier takes up all the CPU for no real reason.

```
sudo killall update-notifier
```

---

### Post by Yv12345vY on 2005-12-23
[QUOTE=fordfan753]I've seen problems on lots of machines where the update-notifier takes up all the CPU for no real reason.

```
sudo killall update-notifier
```[/QUOTE]

Not sure if that is doing anything for me yet although I did run the command a bunch of times.  I'll let you know if I notice any performance differences.

---

### Post by Yv12345vY on 2005-12-23
Hi Benchrest,

What I did at first was 
```
ps aux | grep power
``` and
```
ps aux | grep acpi
```
then I would simply kill all the processes started by root with lowest ID numbers using
```
sudo kill ####
```

But, use synaptic ```
sudo synaptic
``` or go to System > Administration > Synaptic Package Manager.  For right now I removed everything ACPI and power related.  I also moved to a 686 kernel and things are faster I think.  The CPU isn't always loaded and the hdd isn't spinning constantly.  From here on it's just a matter of trying to narrow down to what is actually causing the slugginess.

I hope this helps!

[QUOTE=Benchrest]I am not hijacking this thread but I have simaler problem. But not every boot. Try rebooting and see if it happens every boot. It will show 100% cpu but the only heavy use application is the system monitor just like yours. It will show about 45%. Where is the rest used? I need more research before opening my own problem, but **where do you find the power management setting you mentioned**? By the way, if I reboot the system is fine. I only notice this on my laptop that has no battery installed and is running on AC.[/QUOTE]

---

### Post by Yv12345vY on 2007-11-02
This is long overdue but adding "mem=512M" or "mem=768M" to boot parameters solved this problem!

---

### Post by NJC on 2007-11-02
What does adding "mem" to Grub do? I tried searching for info on that parameter but no dice.

---

