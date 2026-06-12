---
title: "KDE 4.9 crashes in ubuntu 12.10"
date: 2012-11-28
forum: Desktop Environments
---

### Post by Hotshot5000 on 2012-11-28
When the system is under heavy load and uses almost all memory (including swap) my taskbar and window decorations disappear. Is this kwin dying on me? After this happens I cannot do anything with the remaining windows and cannot start a terminal so I have to kill X and restart lightdm. I cannot report it as a bug since I don't have a real error happening and I am not sure that I can helpful with this kind of report so I am asking if anyone else is getting this behavior.

---

### Post by khelben1979 on 2012-11-28
Seems to me that getting more RAM is the solution, or try another desktop enviroment which requires less RAM. 

As from what I've read from KDE and the developments they have made, it has gotten bigger and more sluggish by the years, needing more RAM because of all the KDE software and components has increased in size.

---

### Post by Hotshot5000 on 2012-11-28
But it doesn't get to the limit. I have 3GB of RAM and 3GB swap. When Ram is around 2.8 and swap around 2.3 I notice that bugs start to creep in and after a while kwin and everything crashes.

---

### Post by nmaster on 2012-11-28
you could try the package kubuntu-low-fat-settings to minimize your memory usage.
```

sudo apt-get install kubuntu-low-fat-settings

```

---

### Post by haqking on 2012-11-28
> **Hotshot5000 said:**
> But it doesn't get to the limit. I have 3GB of RAM and 3GB swap. When Ram is around 2.8 and swap around 2.3 I notice that bugs start to creep in and after a while kwin and everything crashes.

So you are saying when both your RAM and SWAP are almost used up things get sluggish ? go figure ;-)

Get more ram, increase swap, tone down KDE or use a lighterweight desktop.

I use KDE and it is blisteringly fast, I have 16Gb but currently i have full KDE eye candy and have 6 tabs open in Firefox, Clementine playing and KTorrent downloading and I am only sat at using 1.3Gb of RAM so i dont know what you are doing to use all that memory but i suggest optimising things, changing DE or getting more memory.

Cheers

---

### Post by azmyth on 2012-11-28
Do you have Desktop Effects enabled? I would try disabling.

---

### Post by Hotshot5000 on 2012-11-28
What I am trying to say is that if I am using a lot of memory kde crashes. It's not like I use all my memory, there is still 500 MB or more left. It shouldn't crash should it? I understand why it's sluggish, but I don't understand why it crashes.

---

### Post by khelben1979 on 2012-11-29
> **Hotshot5000 said:**
> I don't understand why it crashes.

It could be your graphics driver which causes the instability due to heavy load on the graphics driver, but then again it can be many other things too. In what condition are your PC in? Is it old?

In my opinion, just go for Gnome to see if it solves your issues for starters. And if it does, then you can be sure that the KDE is the source of your problem. Right now it's hard to know for sure what could be wrong with so little information.

Another thing: about the RAM-usage. Linux caches up a lot of data from the software applications, and usually that's not a problem if you have decent control over what software you're using and how your system manages to handle them. As from what you can see from my own signature, I'm very strict on what software applications I use to limit ram usage and to prevent too much software to cache up, to avoid the software slowing everything down.

With my experience using KDE I can tell that I was quite happy with KDE 3.x, but when certain applications crashed, I mostly figured that it was badly written software or that my PC got overheated, needing better cooling in my case.

---

### Post by Hotshot5000 on 2012-11-29
I experience no crashes in xfce or gnome 3 and gnome fallback with compiz under similar load. Unity does crash on me even if the system is not under heavy load but then again it's a new technology.

---

