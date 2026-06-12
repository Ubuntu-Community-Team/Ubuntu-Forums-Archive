---
title: "Gaming Question"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by delphiguy on 2007-07-18
Cheers,

Since the announcement of StartCraft2, took my StarCraft cds and made an ISO image of them,
and installed it via wine.

Now whenever I wanted to play StarCraft all I have to do is mount the ISO to /media/cdrom0 and 
disable Beryl.  And when Im done playing I just umount the ISO and active beryl again.

Now my question is that is there a way for me to automate this process? I mean can I make a launcher on
my Desktop that when I click on it, it mounts the ISO and disable Beryl, and load StarCraft.  And after playing, upon closing of StarCraft, the ISO umounts and activates Beryl again.

Thanks.

---

### Post by borris.morris on 2007-07-19
The first part would be somewhat easy. Just change the launcher to "killall beryl | mount /path/to/iso /media/cdrom0 | wine C:/Program Files/path to starcraft". That's an estimate. You should run it in a terminal to see if you get errors for the first part.

---

### Post by delphiguy on 2007-07-19
thanks I'll that out.

---

### Post by frodon on 2007-07-19
It is possible but i think it is more simple to just run your game on another display thus you don't touch beryl and can swich between the game and your desktop whenever you want.

You will find instructions for this here :
[http://ubuntuforums.org/showthread.php?t=493025](http://ubuntuforums.org/showthread.php?t=493025)

---

### Post by delphiguy on 2007-07-19
wow, i didnt think that possible... thanks for tip, ill go check it out now.

---

