---
title: "Nvidia 180 driver problem"
date: 2009-01-05
forum: General Help
---

### Post by Valok on 2009-01-05
So I recently decided I would give the 180 driver series a try because I'd heard nothing but good about them.  I followed a set of instructions over at the community cafe which was the following:

1-Go to system-->administration-->software sources, deselect universe, go to third party software, add:
Quote:
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jaunty main universe
2-Close and reload sources
3-Open a terminal and type: sudo apt-get install nvidia-glx-180
4-IMPORTANT: Go back to software sources and undo the changes, close and reload
5-Reboot



After doing that I restarted my computer and when it came back up my graphics were all screwy.  I can't turn on any compiz effects, and I can't change my resolution to anything higher than 800x600.  

Any help or advice would be greatly appreciated.

---

### Post by northern lights on 2009-01-05
> **Valok said:**
> Any help or advice would be greatly appreciated.Revert back to nvidia-glx-177:

```
sudo aptitude purge nvidia-glx-180 && sudo apt-get update && sudo apt-get install nvidia-glx-177
```

nvidia itsself does not yet offer any 180.XX.XX for download. Check [here]("http://www.nvidia.com/object/unix.html").

---

### Post by Valok on 2009-01-05
Is that the stock one that gets installed when you do a fresh install?

If I could get things back to that for now I'll probably check out Envy and just use that for my updates.

---

### Post by northern lights on 2009-01-05
Depending on what nvidia device you're using, it might be "the stock one". If your card is fairly new (4th generation GeForce and above) it would be.

Post the output of```
sudo lshw -C display
```for further information on that.

Why would you want anything else, by the way?

Why envy, if your device worked out of the box?

---

### Post by Valok on 2009-01-05
I've just heard that there are a couple performance increases with the newer cards, and me being a gamer I like to get every bit out of my games that I can.  Was gonna give these drivers a try and see if anything changed, but if it ends up being too much of a hassle I won't bother.

---

### Post by northern lights on 2009-01-05
> **Valok said:**
> I've just heard that there are a couple performance increases with the newer cards, and me being a gamer I like to get every bit out of my games that I can.  Was gonna give these drivers a try and see if anything changed, but if it ends up being too much of a hassle I won't bother.
Gotcha. While I don't play games too much, I like to be on the bleeding edge and often can't resist possible performance tweaks.

But in this case, nvidia, who release the driver themselves, is not offering them on their public download website, and they're in the jaunty universe repos (opposed to restricted were finalized drivers would end up).

I haven't read up on the 180 series at all, but I'd assume that in theory they're more efficient (e.g. as far as the functions they call upon are concerned), but are not beyond testing stage. The driver included in jaunty appears to be at most a release candidate if not alpha or beta.

When Jaunty's released in April, it should be a different story.

---

### Post by Valok on 2009-01-05
Well if the drivers are just in a testing state, I might hold off until they come out of that.  In the game that I play mostly now (WoW) I don't really have any performance issues, was just looking for a little boost.

---

### Post by fooman on 2009-01-05
> **northern lights said:**
> nvidia itsself does not yet offer any 180.XX.XX for download. Check [here]("http://www.nvidia.com/object/unix.html").

well,  they do....but they are betas.  and i believe you need a geforce 6xxx series or better.

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

under recommended/beta...choose beta and click "search".

i am using the latest beta with my 8800gt and they are working fine.  no noticeable performance increase that i could tell....but they have been running perfectly stable for me.

---

### Post by Valok on 2009-01-05
Good to hear Fooman, I have the same video card as you do.  (I have 2 of them but as I understand SLI isn't working well in linux).

---

