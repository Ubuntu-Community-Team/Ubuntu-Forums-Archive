---
title: "Manage cpu usage per program"
date: 2010-08-23
forum: Desktop Environments
---

### Post by ubutu on 2010-08-23
Looking for a way to control how much cpu apps are allowed to use. 

I'm 10.04 64bit dual core.

---

### Post by scorp123 on 2010-08-23
There is a command-line program called "renice" which can control what priority programs get ... or not. Usually it should not be necessary to mess with this.

I recommend reading the manual:
```
man renice
```

(use your cursor keys to navigate; use "q" to quit)

---

### Post by ubutu on 2010-08-23
Thanx
I guess I should have specified I wanted a particular app to have no more than rather than prioritized........if there's a difference:-|

```
http://gutsywww.ubuntuforums.org/showthread.php?t=992706
```

---

### Post by scorp123 on 2010-08-24
> **ubutu said:**
>  to have no more than rather than prioritized....... Setting process priorities works both ways :D  You can increase a process priority (by giving it a negative number; e.g. -20 is the max.) ... or decrease it (by giving it a positive number; e.g. processes with a 'nice' value of +20 will be slow like snails), depending on what you need. The logic here being that setting a priority of -20 is *"not nice"* (not at all!!) for other users and other tasks on the same system because you are taking CPU and I/O cycles away from their tasks, hence why giving a process a negative number will actually increase its priority in the system. On the other hand giving a positive number such as +20 to a task is *"nice"* (waaaaay too nice actually ...) because you are giving CPU and I/O cycles away ... Those values +20/-20 are the biggest values you can set and very extreme. Depending on what you do you can bring your system down to a screeching halt just by giving the wrong tasks the wrong priorities ... So I'd recommend you don't go beyond -5/+5 unless you really really know what you're doing. If you google "Linux renice" there are a few good examples out there on how to squeeze out a bit of a performance gain for certain tasks ...

> **ubutu said:**
> 
```
http://gutsywww.ubuntuforums.org/showthread.php?t=992706
``` That looks useful, especially for servers IMHO. Thank you. I had to bookmark that one. :D

On a desktop with a user sitting in front of the system I'd say this is a bit of overkill ... but OK, if you have background tasks running that regularly spins out of control ... why not? Or maybe you can use a combo and use "renice" as well.

Maybe you're also interested to know that there is a command called "taskset" ..? With that one you can force programs to stay on a specific CPU. Usually it should not be needed and the Linux kernel should automatically choose which CPU core should work on which process ... but there could be occasions where you don't want a program to spin out of control and e.g. occupy all 4 x CPU cores in your system? So with "taskset" you can tell a process to stay on a specific CPU core.

I have only rarely used it ... but the syntax is e.g.:
```
sudo taskset -c 2,3 123456
```

This would tell the process with the PID '123456' to stay on CPU cores 2 and 3, but not bother 1 and 4 ...

As I said: Usually you shouldn't need to do this as the Linux kernel is designed to take care of this automatically ... but the option is there if you really need it.

---

### Post by ankspo71 on 2010-08-24
> **ubutu said:**
> Thanx
I guess I should have specified I wanted a particular app to have no more than rather than prioritized........if there's a difference:-|

```
http://gutsywww.ubuntuforums.org/showthread.php?t=992706
```

I think I understand what you are asking, but as far as I know it isn't possible to set a maximum cpu usage per application. In my opinion, if we were able to to that, setting a value for an application could cause it to freeze when it reaches that specified point. 

This is where the 'nice' (priority) settings come in handy. 

By default, downloading with transmission will tie up my network traffic to the point of not being able to browse the internet, but if I run transmission with a different nice value (a lower priority), it has an incredible improvement on my internet experience.

Here is an example of me using transmission with a lower priority:
```
nice -n 3 transmission -m
```
"nice -n 3" sets the value, and -m is a transmission option to start minimized. 
Hope this helps.

---

### Post by scorp123 on 2010-08-25
> **ankspo71 said:**
> ```
nice -n 3 transmission -m
``` Good idea + nice trick :D

---

### Post by ubutu on 2010-08-25
> **scorp123 said:**
> On a desktop with a user sitting in front of the system I'd say this is a bit of overkill ... but OK, if you have background tasks running that regularly spins out of control ... why not? Or maybe you can use a combo and use "renice" as well.

I do have several Virtual Machines running simultaneously and wanted a set amount of CPU per each instance.


@ankspo71..........I haven't tried cpulimit  yet, here's a quote.........."Daemon runs in background and checks if some process is consuming more  then 20% of CPU and if it does then daemon lowers CPU consumption of  particular process to maximum of 20%. The goal is to have no single  process that consumes more then 20% of CPU power."


Am now searching forum on how to maximize VMware and 10.04.

---

### Post by kpkeerthi on 2010-08-25
> **ankspo71 said:**
> 
By default, downloading with transmission will tie up my network traffic to the point of not being able to browse the internet
You may be choking your router/modem by allowing Transmission to have too many open connections at a time. (I use Ktorrent but) I presume Transmission should have an option to tame down the number of open connections. In Bittorrent world, lot of open connections doesn't necessarily mean faster downloads. You might want to tweak it (reduce) down a bit until you hit a sweet spot.

---

### Post by mcduck on 2010-08-25
> **kpkeerthi said:**
> You may be choking your router/modem by allowing Transmission to have too many open connections at a time. (I use Ktorrent but) I presume Transmission should have an option to tame down the number of open connections. In Bittorrent world, lot of open connections doesn't necessarily mean faster downloads. You might want to tweak it (reduce) down a bit until you hit a sweet spot.

In addition to the amount of connections it might be necessary to limit the upload, and perhaps even the download speed, a bit. But that depends on the type of your Internet connection so you'll need to experiment a bit until you find settings that work best.

I haven't used Transmission on Linux lately, but at least the OS X version also has a speed limit mode that allows you to toggle even stricter limits on and off with a single button.

What comes to nice, did you know that it can also be used with *users* and *groups* and not just with processes? That if something teaches us that you should never make your system admin angry, or you might find out that everything you try to do suddenly takes a very long time... ;)

---

