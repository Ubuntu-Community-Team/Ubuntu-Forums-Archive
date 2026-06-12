---
title: "Slow , stuttering"
date: 2008-12-10
forum: General Help
---

### Post by Itlandm on 2008-12-10
For the last year or so I have this problem on my HP pavilion ze5600 laptop. Music and scrolling stutter, even with less than full CPU and memory load. The exception was one day when I booted without network and connected to the network later, but this never worked again.
I removed IPv6 support thinking it may be the culprit, but no. I deleted my ATI driver and the xorg process is now down from around 35-40 to 5-15 for the most part, but the stuttering is still there. What am I missing?

---

### Post by ajcham on 2008-12-10
Are you running Compiz?  If so, disabling it may help.

---

### Post by Itlandm on 2008-12-11
I use Metacity, and it seems to use only marginal CPU and memory. I now tried replacing with Compiz, and it does indeed stutter even more. Even then, only 65% of CPU was used, but the system seems to believe otherwise.

A friend says there is a scheduler or some such now that believes it runs on a dual-core processor, even though it does not. But if so, this problem would probably affect thousands of people and draw a lot of attention.

I guess it is time to back up the home directory and try a different version. I am not looking forward to it, being an absolute Linux amateur.

---

### Post by ajcham on 2008-12-11
> A friend says there is a scheduler or some such now that believes it runs on a dual-core processor, even though it does not. But if so, this problem would probably affect thousands of people and draw a lot of attention.

I think your observation is accurate - if that was the problem more people would have noticed it.

How much Swap is being used during normal use of the computer?  That might be worth looking at.

---

### Post by Itlandm on 2008-12-12
With Opera, Banshee and OpenOffice, it uses 4.6MB of swap file, but it uses only 55% of physical memory and the hard disk light only rarely flickers. It does not seem to be any shortage of either processor, memory or disk space. Back when I did some programming, in the days of MS-DOS 3, I remember we sometimes had problems with less obvious resources such as interrupt requests.  But I have not kept up with the times, as it were, so I don't know how modern operating systems do this.

---

### Post by Itlandm on 2008-12-15
I downloaded the Kubuntu packages to see if this made a difference. The Amarok music player does not stutter as easily as Audacious, Banshee and Rhythmbox. Under normal load it plays normally even while I write in another program. This holds true even when started from a Gnome session. While this does not restore the smoothness and quickness I experienced earlier, it us a workaround of sorts.

---

