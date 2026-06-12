---
title: "Nethack recovery"
date: 2008-01-18
forum: Gaming &amp; Leisure
---

### Post by Daneel24 on 2008-01-18
I've been playing Nethack-QT and ran into a few problems. The first one happens more or less constantly, but was easily fixed thanks to this thread:
[http://ubuntuforums.org/showthread.php?p=2042442](http://ubuntuforums.org/showthread.php?p=2042442)

The second is that the game tends to slow the computer down horribly after playing for for a while, this could be fixed by restarting it. However I now made the mistake of just waiting to see what happens and the computer simply hanged and I had to reboot. 

I got down to level 25 with this character so wouldn't like to lose it that easily, and I found out Nethack has this nice little recover program. But of course it doesn't work. I try writing:

*vasya@Router12:/usr/lib/games/nethack$ sudo recover -d /var/games/nethack 1000vasya.67*

And I get this response:
> Recover v1.3b by Tom Pycke

Scanning devices...
Ext2 devices:
recover: No valid standard devices found; are you a privileged user?

If your device is not listed, you can still use it
*** stack smashing detected ***: recover terminated
Aborted

I get this even if I just write "sudo recover". 

I'm running Gutsy on a 300mhz Dell Latitude laptop and I'm still pretty much a newbie to Unix, I have no idea what this might mean. Could anyone give me a clue?

---

### Post by Helios38 on 2008-01-28
300 mhz? wow. must be annoying to start up that laptop.


have you tried reinstalling nethack?

maybe a file just went corrupt.

---

### Post by joeyjoejo on 2008-06-11
hey man,

My girlfriend was just in this possition and I've had to figure out how to use the recover app for nethack (I should say thanks because your post was really helpful for tracking down the files I needed, cheers mate) anyway, if you still have the temp files you need for this (I.e. If you've not started a new game between now and then you can probably still get it back... Or at least it might be helpful in the future.

Anyway, all you needed to do was to run the executable from the dicectory you were in as root, for me this meant;

cd /usr/lib/games/nethack 
sudo ./recover -d /var/games/nethack 1000joe

(obviously you know this bit but for someone paniking after losing their game it might be helpful)  The 1000 is the uid of your shell, which you can find by running something from bash, if you google for find uid bash it should tell you the command, most uids seem to be 1000 (ymmv) and joe is the name of my computers nethack characters (yours is obviously different) 

What was going on with you about the ext2 thing was that you were trying to run the recover programme which is "system wide", as it were. The ./ says that you want to use the nethack recover which is in that folder 

Anyway, I hope this helps someone, even if you have lost that game... Also I think it might have been a similar problem that got the game of nethack at my end... Whenever we play the CPU usage goes up to about 100% and most of that is nethack, even after its been quit! The game itself reported a segmentation fault, but I wouldn't have expect a game as old and stable as nethack to segfault anymore... Its a pickle. When I've got more time I'll try and pin down why this happens (I'm running the latest version of ubuntu and the latest nethack, but it happened on fedora 8 too, but not when only running bash sans GUI)


Cheers,
joe

---

### Post by mrmooge88 on 2009-05-03
Thanks Joeyjoejo for the fix. I had the same problem. I wish I would've know about this earier.

---

