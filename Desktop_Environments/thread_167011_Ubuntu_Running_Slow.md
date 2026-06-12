---
title: "Ubuntu Running Slow"
date: 2006-04-27
forum: Desktop Environments
---

### Post by YaNoS on 2006-04-27
I've just installed Ubuntu and it has been running really slow.
I have a AMD Sempron 2.8(with clock set at 1.6) and 2GB DDR 400mhz memory, nvidia Geforce 6600 GT video card so I think my PC isn't the problem, as Windows was running OK
I installed Ubuntu in a separate partition that has 7 GB

I'm unsure if my processor holds 64 bit tecnology, if so, could it be this slow because I didn't install the 64bit version?
Should I try testing it with a LiveCD?

Thanks in advance :D

---

### Post by Qrk on 2006-04-27
You can do several things to speed it up. 

1) Install 3-d drivers for your graphics card. (for you, it is nvidia-glx)

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

2) Install the package linux-k7, which will give you kernel more optimized for your processor. 

```
sudo apt-get install linux-k7
```

3)If you still have a problem try running the command *top* or go to System->Administration->System monitor and see if an application is taking up too much cpu. X.org might be the biggest hog, but it shouldn't be over 10%

---

### Post by louis_nichols on 2006-04-27
Did you install the proprietary nvidia drivers for your video card (instructions [here]("http://ubuntuforums.org/showthread.php?t=75074"))? Also, are you using optical drives without having enabled dma (instructions [here]("http://ubuntuforums.org/showthread.php?t=163855"))?

They are both elements which, in my experience, have caused a slow system.

---

### Post by YaNoS on 2006-04-27
Wow guys, thanks a bunch!

I'll try all that and then reply  :-D

Edit:
Hey, I tried updating my drivers and it seems O.K. for now!
Thanks alot!

---

### Post by louis_nichols on 2006-04-28
[QUOTE=YaNoS]Wow guys, thanks a bunch!

I'll try all that and then reply  :-D

Edit:
Hey, I tried updating my drivers and it seems O.K. for now!
Thanks alot![/QUOTE]

Did you TRY updating or really update? :p :)
(joke. no offence!)

Glad it's better now.

---

### Post by YaNoS on 2006-04-28
Jesus!

It's horrible to kinda revive this topic but I just checked the system monitor and it was jumping from** _90.0%_** to **_97.6%_** of ***_CPU usage_***!! :-k

Fixed :D

---

### Post by ububaba on 2006-04-30
[QUOTE=YaNoS]Jesus!

It's horrible to kinda revive this topic but I just checked the system monitor and it was jumping from** _90.0%_** to **_97.6%_** of ***_CPU usage_***!! :-k

Fixed :D[/QUOTE]
Where/how does one check CPU usage? This query, no joke either.:-?

---

### Post by bluevoodoo1 on 2006-04-30
[QUOTE=ububaba]Where/how does one check CPU usage? This query, no joke either.:-?[/QUOTE]

```
gnome-system-monitor
```

or a third-party application like conky or gkrellm.

Conky is my personal choice.

---

### Post by Ramses de Norre on 2006-04-30
applications > system tools > system monitor
Or in terminal use top (shows the cpu load better because sys monitors gui uses quiet a lot cpu).

---

### Post by ububaba on 2006-04-30
Thanks for such a quick response. 

Another one: How/where does one indicate *Report Bad Posts*?

Thanks in advance!

---

