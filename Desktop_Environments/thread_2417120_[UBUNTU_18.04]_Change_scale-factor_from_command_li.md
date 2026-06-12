---
title: "[UBUNTU 18.04] Change scale-factor from command line is not working"
date: 2019-04-21
forum: Desktop Environments
---

### Post by aibix on 2019-04-21
I have the same problem.

I can set a good scaling via 

```
xrandr --output eDP-1 --fb 3840x2160 --scale 1.5x1.5 --mode 1920x1080 --dpi 165.63
```

on my Dell XPS 13 (FHD screen), but then all is very small until i set 200% in settings. After that it looks just perfect, almost like a Macbook, not blurry at all.
Sadly, when setting the xrandr string Gnome will revert to 100% (which is reflected in monitors.xml) and i have to manually set it again vie settings, cause it won't save the value with

```
gsettings set org.gnome.desktop.interface scaling-factor 2
```

What command will set the appropriate scaling in settings to 200%? There has to be one - and someone who knows ...

best regards
Gerd

---

### Post by wildmanne39 on 2019-04-21
Moved to own thread from:

[https://ubuntuforums.org/showthread.php?t=2391925](https://ubuntuforums.org/showthread.php?t=2391925)

Please always start your own thread instead of posting in someone else's for help.

Thanks!

---

### Post by aibix on 2019-04-21
Why? It was exactly on topic and would have helped me and the two prior posters if someone answered (all would probably be notified).

---

### Post by wildmanne39 on 2019-04-21
1. Even though it appears you have the same issue most of the time the cause is different.

2. It is confusing for the people being helped and the person helping when more then one person is receiving help in a thread especially when most of the time the cause of the issue is different for each person.

3. This thread is a few days from being a year old and there is a rule against posting in an old thread, when the thread reached a year without a post it would have been closed automatically by the forum software, the OP has not been back in all this time so he either resolved the issue or changed operating systems or just gave up.

4. When searchers are looking for answers to there issue, it helps when the thread is marked solved, only the person that starts the thread can mark it solved and so even if you found an answer in the other thread it would never be marked solved.

5. It is considered hijacking someone else's thread and is very rude.

---

