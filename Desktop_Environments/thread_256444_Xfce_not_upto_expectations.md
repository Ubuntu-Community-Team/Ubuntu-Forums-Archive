---
title: "Xfce not upto expectations"
date: 2006-09-13
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-09-13
Hello,i have gnome,xfce and KDE installed.I found that astonishingly,xfce utilised as much memory as gnome.Isn't xfce supposed to use less resources??Or is gnome made to utilize less memory?

---

### Post by akshaysrinivasan on 2006-09-13
Another surprise,KDE takes the same amount of memory as both of them ,with all the window transparencies turned on!Instead of xfce i suppose KDE is better for low end systems.

---

### Post by Jussi Kukkonen on 2006-09-13
Anecdotal maybe, but: 

As the owner of a couple of low end systems (128MB or less) I can tell you that in reality xfce outperforms Gnome and KDE.

---

### Post by chavo on 2006-09-13
I think this has a lot to do with the way Linux uses memory and the way most tools report memory usage. [Here's]("http://ktown.kde.org/~seli/memory/") a test of some desktop environments and their memory usage. Xfce comes out on top in pretty much every test. Of course that comes with giving up a lot of features. And you can see that KDE actually uses a lot less resources than Gnome, a lot of people assume that it's the other way around. Because GNOME is lacking in features they assume it is less of a resource hog.

So basically the point is Linux will use all your RAM, no matter which desktop you use or how much RAM you have. That's just the way Linux memory management works, it caches a lot of stuff and gives up the RAM when apps request it.

---

### Post by akshaysrinivasan on 2006-09-14
I found the cuilprit.It was the gtk-xfce-engine which was hogging much of the memory.Now that i've removed it everything is going nicely.

---

### Post by akshaysrinivasan on 2006-09-14
Still not even xfce is comparable with the robust enlightenment!

---

### Post by akshaysrinivasan on 2006-09-14
Now i have statistics to support my answer.I used the default desktop(i created a new user) and ran xterm and asmem to check the memory consumption.The results :-
              Physical         Swap
Gnome          58%              8%
Enlightenment  37%              8%
KDE            51%              8%
XFCE           56%!             8%

---

