---
title: "kubuntu boots and runs VERY slow on dimension 2400"
date: 2009-01-02
forum: General Help
---

### Post by Jon Redbeard on 2009-01-02
Hello, I fix windows for a living but am new to linux. After playing with kubuntu for a couple days I'm really liking it and once I know how to use it better I will most likely switch to it full time at home. The main problem I'm having so far is that kubuntu runs VERY slow on my friends Dimension 2400, even slower than xp did previously. If xp had run slowly on this machine as well I would assume it was due to the speed of the hardware, but win xp ran everything at decent speed and pretty responsive in general. As I write this I'm trying to install Mandriva for dual-booting to see if it runs any faster. Any help would be greatly appreciated and if this has been solved elsewhere on the forum I'm sorry but I couldn't find it.

Celeron 2.4ghz processor
256mb ram
intel 845gv onboard video

---

### Post by Open-SuSe-A-Me on 2009-01-02
Are you using Hardy (kde3) or Intrepid (kde4)?

256 Ram might be the problem, did you make a swap partition when you installed kubuntu?  Do you know how large the swap is?

I also have a dimension 2400, but i added extra ram to mine, i now have 1.5G.

---

### Post by Jon Redbeard on 2009-01-02
Thanks for the reply! I'm using the one with kde 4.x. I left pretty much all the install options as default so unless a swap partition is setup by default I don't have it (how would I check from within kubuntu?). The ram issue could be the problem but Win XP ran quite well and I would have thought kubuntu would be less memory hungry than XP, kde front-end or otherwise. If it helps, I've tried installing both of the newest versions of ubuntu before this and Mandriva just a little while ago, all of them failed. They all get to a certain point, either booting from cd or during the install, where they go to a black screen with the cursor in the middle, and lock up. Just ask if there's anything else I can tell you that would help.

---

### Post by Open-SuSe-A-Me on 2009-01-02
I believe you need a little bit more Ram (over 300 i think) to be able to install from most of the Ubuntu cd's, this is why they also have the "alternate install" ISO images available, and thats probably why some of your installations failed.

If you did an install and let the installer choose the partition settings than yes you have a swap, the default behavior is to create one.  

I haven't fooled around with KDE 4.x much because i don't like it at all compared to 3, so i am not exactly sure how to determine the size of your swap.

I would suggest following the instructions in the first post here [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)  to set your swappiness to maximum.  The swap is similar to the pagefile in windows but more efficient.  By setting your swappiness to maximum your computer will swap as much and as early as possible because you have a small amount of ram, and this should improve your performance.

Have you tried the default Ubuntu install with Gnome instead of KDE? If so, how fast did that run?

---

### Post by Jon Redbeard on 2009-01-02
Ubuntu with gnome was one of the failed installs I mentioned. I'll try changing the swap settings as mentioned. By the way, why would kubuntu or any other linux distribution run slower than xp on the same machine? From the very admittedly small amount I know so far it seems like linux would be faster.

---

### Post by Open-SuSe-A-Me on 2009-01-02
It usually runs faster from my experiences.  If KDE4 is your first Linux experience, i will say that it is much different from Gnome and much different than its predecessor, KDE3.  Its possible that the "plasma" and other KDE4 eye candy may be slowing your machine down, it is pretty new anyway.

I suggest trying either the Intrepid alternate install disc (with gnome) or the Kubuntu Hardy 8.04 alternate install disc.  There is also Xubuntu which uses XFCE desktop environment which is designed for under 512 ram and/or older computers.  XFCE is basically a much lighter Gnome.

My guess is that KDE4 caught your machine off guard.


Welcome to the Linux side of things!

---

### Post by Jon Redbeard on 2009-01-02
Well, I think I'll just try kde 3 instead of fooling with this any longer. This is for a friend anyway. M y own computer is a lttle better than this, so maybe I'll try the newer kde on it. Thanks again :D

---

### Post by Open-SuSe-A-Me on 2009-01-02
No problem!

If you try KDE4 on your own machine and like it, more power to you.  But I would say that since it is your first Linux experience you *may* want to use a different environment at least at first, because KDE4 is still a little bit buggier than the others and lacks some of the functionality of KDE3/Gnome/XFCE right now.  But it is in active development so this should change within the coming months.

---

