---
title: "What is sucking up all my RAM?"
date: 2009-06-11
forum: General Help
---

### Post by geokker on 2009-06-11
I've been using my PC for about 6 hours today. I have 10 applications open the fattest being open office Calc (which I haven't actively used for 5 hours). Top tells me that I've soaked up all my physical ram (4GB) and that I'm using 10% of swap. It also tells me that 8 of the active processes are owned by my user account and that they account for 5% of the memory. All the rest of the process entries appear to be 0.0% memory and are owned by root. Htop concurs as does 'free -m'.

What gives? It's as if the system slowly rots through the day, memory leak style. If I kill all the open processes, nothing much changes except the physical RAM usage dies down a little - swap is still being used. There are 113 tasks still running but surely not 3.6GB worth.

Is there a program out there that makes all this easier to understand?

---

### Post by gradinaruvasile on 2009-06-11
Run top, press shift-o then q, this will order the processes by used memory. Look at the RES (resident) column (that is the amount of memory the processes are using).

---

### Post by geokker on 2009-06-11
What's the 'VIRT' column? For instance, Opera is reportedly soaking up 268m RES (which I assume means megabytes) and a whopping 599m VIRT yet only 10MB of swap is being used.

---

### Post by gradinaruvasile on 2009-06-11
Read this:

[http://www.linuxforums.org/misc/using_top_more_efficiently_3.html]("http://www.linuxforums.org/misc/using_top_more_efficiently_3.html")
A lot of the memory can be buffered or something. It will be freed up if needed. Bet if u open the System monitor (gnome-system-monitor) it will report much higher mem availability.

---

### Post by balloooza on 2009-06-11
Hear is somthing I have noticed with top, at least when working with audio, the locked memory (memlock) will show up as used in top, but the correct term is "wiered" I belive, meaning there is no possible way it can be used by anything other than audio apps, now this may seem irrelevant, but my best place to check has accualy been gnome-activity monitor, it shows the correct ammount of memory that is being used, the other thing to look for is somthing called dbus, this at one time in my life, sucked up memory constantly, and after looking at what it was doing, it was more of a panic than an overload, and soon enough, the system shut down, because of this "panic"

I am not sure what is the problem here, but this may help anyone who is reading this later might have this problem.

---

### Post by geokker on 2009-06-11
It looks like I'm not going to get away without having to do some reading ;)

I wonder what people in the 32bit world do with their paltry 3GB RAM ceiling..

Thanks all.

---

### Post by lovinglinux on 2009-06-11
> **geokker said:**
> It looks like I'm not going to get away without having to do some reading ;)

I wonder what people in the 32bit world do with their paltry 3GB RAM ceiling..

Thanks all.

I have 2Gb RAM on a 32 bit machine. Most of my RAM is used by cache and swap is rarely used. For example right now only 59% of memory is being used by applications and 36% is used by cache. Swap is not even used on this scenario.

If you want to clean up some memory used by the cache you can run this on a terminal:

```
sudo echo "starting..." && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

Most users here will argue that this is not necessary, because Linux memory management is efficient and free memory is wasted memory. Nevertheless, after a few hours running a few applications, my memory becomes fully used by the cache and performance drops. So I use that command to speed up the system a little bit.

You can reduce the swap usage with swappiness. Check [this link](http://ubuntuforums.org/showpost.php?p=7410554&postcount=2) to know how.

---

### Post by geokker on 2009-06-15
I've lowered swappiness to 0 and I swear I can feel a difference - the whole system seem snappier!

---

