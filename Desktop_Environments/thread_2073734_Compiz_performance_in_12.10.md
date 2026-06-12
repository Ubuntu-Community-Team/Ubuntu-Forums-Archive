---
title: "Compiz performance in 12.10"
date: 2012-10-20
forum: Desktop Environments
---

### Post by foobar66 on 2012-10-20
Yesterday I installed 12.10 in a separate partition.
I have noticed that compiz is taking a huge amount of cpu (constantly around 20%).
Compared it with 12.04 and there compiz is taking 2% ...
That's on a fresh clean install.
Any hints/tips are of course welcome but that looks like quite a serious performance degradation. The whole desktop, window management feels sluggish on my hardware (Dell Studio 1537) with 12.10.
I think I'm gonna stick with 12.04 for the time being.

---

### Post by grahammechanical on 2012-10-20
CPU usage does not go above 9% on my 12.10 when I rattle the windows around. There was a Compiz update yesterday. Compiz being worked on all the time. Had several updates during the development cycle.

Regards.

---

### Post by foobar66 on 2012-10-20
> **grahammechanical said:**
> CPU usage does not go above 9% on my 12.10 when I rattle the windows around. There was a Compiz update yesterday. Compiz being worked on all the time. Had several updates during the development cycle.

Regards.

Weird. I also got the update, but still compiz is eating all my CPU when simply moving around 1 single window.

Well, it's the first performance issue since 4 years that I had with Ubuntu ...

---

### Post by kyalpani on 2012-10-20
Compiz is chewing up 4-5% of my cpu permanently (since ubuntu 12.10). This is not really acceptable. I really don't care about 3D effects so I don't see why this is forced upon us. Perhaps there is a way to turn compiz off? Anyone can help?

thx in advance

---

### Post by kyalpani on 2012-10-20
make it around 445-50% now... something triggered it off to just that high and it is staying that way. There is a serious bug in compiz.

---

### Post by foobar66 on 2012-10-21
I found it has something to do with the old compiz configuration from 12.04.
Created a new user account and when I log in into this new account compiz performance is not an issue.

However, when installing 12.10 I had used the same /home partition as on 12.04 (so I was using my 12.04 compiz configuration).

---

### Post by jtrost on 2012-10-23
> **grahammechanical said:**
> CPU usage does not go above 9% on my 12.10 when I rattle the windows around. There was a Compiz update yesterday. Compiz being worked on all the time. Had several updates during the development cycle.

Regards.

Compiz is using 40% of my CPU since this update. I am using 12.04. Any suggestions on how to fix this?

---

### Post by petermolnar on 2012-11-20
This is ridicolous. Yesterday at last I've set up everything, so I believed, it was fast, snappy and as it should be. 
This morning starting in powersave mode CPU and EVERYTHING become blurry, slow, this is just nonsense.
Cinnamon wipes the floor with Unity when it comes to speed, Gnome3 as well.

The real problem is that I'm unable to find any solutions; even a change fixes it, it will not last too long and the system is completely unuseable if not running with full CPU power.

---

### Post by Paddy Landau on 2012-11-20
I have found that running 12.04 in VirtualBox is snappy; but running 12.10 in VirtualBox is surreal because of the slowness (same resources allocated to each machine).

There is definitely something wrong.

---

### Post by markbl on 2012-11-20
> **Paddy Landau said:**
> I have found that running 12.04 in VirtualBox is snappy; but running 12.10 in VirtualBox is surreal because of the slowness (same resources allocated to each machine).

There is definitely something wrong.
That's because currently Virtualbox 4.2.4 does not support 3D acceleration in ubuntu 12.10 guests due to an incompatability with xorg 1.13. The VB team are working on it.

---

### Post by Paddy Landau on 2012-11-21
> **markbl said:**
> That's because currently Virtualbox 4.2.4 does not support 3D acceleration in ubuntu 12.10 guests due to an incompatability with xorg 1.13. The VB team are working on it.
Thanks for the clarification. I shall bear that in mind.

---

