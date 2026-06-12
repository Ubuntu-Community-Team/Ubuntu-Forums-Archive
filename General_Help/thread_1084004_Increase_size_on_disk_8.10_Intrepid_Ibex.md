---
title: "Increase size on disk?? 8.10 Intrepid Ibex"
date: 2009-03-01
forum: General Help
---

### Post by Shatford on 2009-03-01
Hello guys,

I just recently installed Ubuntu, mostly because of the good reviews I heard and that I was a bit finished with Windows.

I didn't think I would be going to use it very much, cause I thought it would be too difficult, but now I love it.

The only thing that's a bit shitty is that when I installed it, I choose for the max. 8 gig installation.

Now I would like to change that cause I would like to use it a bit more, and the 8 gig isn't enough because it keeps on telling me I don't have enough space left.

so: I used the 8 gig and i would like to increase that size.
I'm using Ubuntu 8.10 Intrepid Ibex, and i've installed it via Windows. 

I'm not that well known with all the ubuntu stuff yet, so if someone could help me with how to increase the size of the partition in not to high tech talk that would be great.

Thanks in Advance,

Steven Shatford

---

### Post by TeoBigusGeekus on 2009-03-01
Boot up with the live cd.
Go to system->administration->partition editor.
If it isn't there, open a terminal and type
```
sudo apt-get install gparted
```.
From there you can do anything you want with your partitions. 

PS: Just be warned that the procedure takes a lot of time.

---

