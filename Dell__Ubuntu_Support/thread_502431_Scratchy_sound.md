---
title: "Scratchy sound"
date: 2007-07-16
forum: Dell  Ubuntu Support
---

### Post by SpykedOne on 2007-07-16
I have a Dell XPS M1710 with a Integrated Sound Blaster® Audigy™ HD Software Edition sound card.   At times when I am watching video file the sound gets scratchy.  Does that have anything to do with the version of Ubuntu I am running, or not having the right drivers for the sound to play properly?  I recently wiped the hard drive (and XP Media Center that came installed on it  Hahaha) and installed Ubuntu 7.04.

System Specs :

Intel Core Duo 2.33 Ghz
2 Gbts Ram
512 MB NVIDIA graphics card
Integrated Sound Blaster® Audigy™ HD Software Edition

---

### Post by Yarbo on 2007-10-30
I have the same problem.

---

### Post by enkoan on 2007-10-31
Me too, I can sound like a DJ scratching on turntables when I move the volume slider up and down in Volume Control.

Debian sound support is worlds better, but Debian confuses the piss out of me as my tech level is quite low...

---

### Post by linuxlizard on 2007-10-31
Try this-
use gedit to make .openalrc with the following line
(define devices '(native))
saved it in my home directory as .openalrc and it works great. No more crackles!

---

