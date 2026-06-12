---
title: "Erratic mouse arrow movements"
date: 2017-12-08
forum: Desktop Environments
---

### Post by cwlj on 2017-12-08
I am running Ubuntu Mate 16.04.4 on an Odroid xu4 SoC board. Yesterday, everything working. On booting today, the mouse arrow behaves strangely, drifting slowing across the screen, continuing to move after the mouse itself has stopped. 
The switch from arrow to insertion bar and back again is slow when moving across underlying windows. I have done all the usual checks, i.e. trying a different mouse, trying different USB ports, rebooting, different mats under mouse,
and have tried different xset mouse parameters.  None of these make any significant difference. I believe the mice are not defective. Yesterday, mouse behaviour was perfect.  Today, the desktop is virtually unusable. Have done some Web
searching but have not found much of relevance.  I suspect some OS internals or settings have gone wrong, but I have not (intentionally) made any changes.  Any clues anyone?

---

### Post by gigamegawatts on 2017-12-09
I have the same board, the same OS, and the same weird mouse behaviour.  It just started today.

I've never seen anything like this before - I don't even know what term to use when Googling it.  So, sorry, I don't have any clues.  

I'm guessing it's something that arrived via a package update, since I haven't installed anything new or made any configuration or hardware changes recently.

Dan.

---

### Post by gigamegawatts on 2017-12-17
It turns out that this is a known problem with the 4.14 kernel.  I guess the kernel running on my XU4 was updated at some point - I didn't even notice.

The mouse problem can be fixed by installed a .deb package created for the Odroid XU4.  See [https://forum.odroid.com/viewtopic.php?f=146&t=28908#p206904](https://forum.odroid.com/viewtopic.php?f=146&t=28908#p206904).  

Dan.

---

