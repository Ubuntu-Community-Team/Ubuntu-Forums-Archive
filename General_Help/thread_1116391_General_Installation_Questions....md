---
title: "General Installation Questions..."
date: 2009-04-04
forum: General Help
---

### Post by Zedday on 2009-04-04
I'm looking at this very helpful guide on how to install the ubuntu OS... [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

it's very well done and very helpful, but it left me with a few questions...

[COLOR="Red"]**1)**[/COLOR]
a) -- on Step 8 (see link ^ ) it says i can install it on a partition, if i do this, it **[COLOR="Red"]WILL NOT[/COLOR]** delete windows, is this correct?

  b) -- on Step 8 (see link ^ ) do i have to previously have my hard drive partitioned in order to install it on a partition, or is this step partitioning it, and installing ubuntu on the partition its making?

**[COLOR="red"]2)[/COLOR]** -- at what step (see link ^ ) would i be able to install ubuntu on an external hard drive, or is this even possible?

[COLOR="red"]**3)**[/COLOR] -- on step 8, as long as i click _"guided - resize"_, there is no way WHATSOEVER i will delete my windows XP, right?

**[COLOR="red"]4)[/COLOR]** -- Am i able to quit the installation process and anytime i wish by clicking _"quit"_ on the bottom right of he screen?



---i'm sorry i ask so much, but i just want to be safe, and it would be much appreciated if you could assist me.

---

### Post by JK3mp on 2009-04-04
Well when it says install it on a partition...then choose the one that windows is NOT on. If you have freespace you should have an option to create new partition. If it doesn't show any freespace b/c all your space is occupied by windows, then you need to use the windows disk managment utility first to shrink your windows partition and find freespace available to set off from windows partition. I believe you can install on external but you have to format it correctly or sum such, lol, not sure never done it. If you use guided install it WILL install on your whole hard drive and WILL delete your windows by default, you must click manual to get to the partition tool where you can create a partition to mount root (main ubuntu etc.) and your swap space (approx. 2x size of RAM ). And you can quit right up to the time you click Install after partitioning. You can try turning off power etc in middle but willl likely corrupt something. Hope this helps, peace.

---

