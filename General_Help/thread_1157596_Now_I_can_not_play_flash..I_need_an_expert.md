---
title: "Now I can not play flash..I need an expert"
date: 2009-05-12
forum: General Help
---

### Post by lsutiger on 2009-05-12
Something is going terribly wrong with my system. I am very sure it is not a hardware problem.
First, [this happened]("http://ubuntuforums.org/showthread.php?t=1155255")(link), then [this happened]("http://ubuntuforums.org/showthread.php?t=1154510")(link).

Now I can not play flash videos (ie youtube). I can see them, and I can start them, but they stop after a second or two.

I have not done any editing to any config files. I installed and removed a couple of packages mentioned in the links to the previous posts, but other than that, notta. I have a very stable system and use it as mainly a web access computer. 

Could anyone give me a heads up on what is going wrong here?

Thanx in advance!

---

### Post by Tipped OuT on 2009-05-12
*Your system is slowly falling apart, piece by piece, it will crumble and the gates of hell will open and engulf the entire universe in viruses and trojans, only mean while, in another dimension, you will be safely at home, sipping your morning Joe, while reading the news paper comics...*

Nah, just relax. Probably an easy fix, wait until someone else answers, mean while I'm going to do a little research on what your problem may be. :)

PS: Have you done any updates that could've broke your installation?

EDIT: Try re-installing Adobe's Flash Plug-in in the mean while.

---

### Post by lsutiger on 2009-05-12
Thanx for your nefarious prediction :) 
I have researched a bit but have not come up with much that answers all the questions. The problem with the update manager really makes me think...that is strange

---

### Post by Tipped OuT on 2009-05-12
OKAY, guessing by your "Problem with update" thread, your installation must have broken from a bad update. I'm not an expert, but what I would do is back up my important files and re-install. It's not the best solution, but it's a guarantee fix.

---

### Post by lsutiger on 2009-05-12
New info - I tried to completely remove adobe flash. I received this error message:```
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

What that means, I have no idea..but it sounds serious, lol

The re-installation of flash did not help

---

### Post by Tipped OuT on 2009-05-12
Wow...that is weird. Sorry, but as far as I can tell, your installation is broken, some way, some how, it broke because nothing is working as it should. Just remember, I'm not an expert, so don't take any of my words as a final answer.

---

### Post by sir_nasty on 2009-05-12
[QUOTE=lsutiger;7268210]New info - I tried to completely remove adobe flash. I received this error message:```
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

We could kind of be the blind leading the blind here but I'll take a stab at it....

Is it possible your root drive is full? or it could be related to a reported bug in having to do with the cache, check the link below...

[http://ubuntuforums.org/archive/index.php/t-440883.html](http://ubuntuforums.org/archive/index.php/t-440883.html)

---

### Post by lsutiger on 2009-05-12
> We could kind of be the blind leading the blind here but I'll take a stab at it....

Is it possible your root drive is full? 


You nailed it! df -h reports 0% available. What should I look for to delete?

My / directory and home are on different partitions. The / has a 10 gig and the home is the rest (minus a 2 gig swap)

---

