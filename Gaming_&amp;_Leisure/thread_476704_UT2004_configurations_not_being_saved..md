---
title: "UT2004 configurations not being saved."
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by coarse.sand on 2007-06-17
I've seen people with nearly the same problem on some other forums (ut2004.ini was just missing), but not quite to this extent.

I bought the Unreal Anthology about a week ago and eventually gave up on recompiling unshield-5.3 to work on my amd64 system. Instead, and I know people probably don't want to hear this on a forum, I downloaded a UT2004 iso of the original CD install from the net, since it would have the linux-installer.sh. I still paid for the CD key, so this shouldn't pose a legal problem, though using a UA key might upset an original UT2004 install.

I originally installed it to /usr/local/games, which was a mistake since it made patching a hassle, so I've reinstalled it to my home folder, under ~/games/ut2004. This is where the problem comes up. From what I can tell, the Default.ini and DefUser.ini files aren't being copied to ut2004.ini and User.ini respectively when the game first starts up. This causes a crash where an engine line in the ut2004.ini is missing. At first I just copied Default.ini and renamed it ut2004.ini (same with User.ini later, because I wanted the key bindings), which solved the initial start up problem, but Ive since hit another wall. After setting all of my configurations, like high detail graphics options and a larger resolution, when I quit the game it doesn't save these changes to the ut2004.ini or User.ini files, so everytime I load the game I have to go back to settings and change all of my options back to what I want. This a) takes a long time, and b) is just really dumb. It's happened both before and after patching with the Epic MegaPack (ECE and 3369 patches).

Does anyone have any idea how to solve this? The game is playable, but if it does this I'm not actually going to play it.

---

### Post by aidanr on 2007-06-17
strange, i'd first try

```
sudo chown -R `whoami` ~/games/ut2004/
sudo chmod -R 755 ~/games/ut2004
sudo rm -R ~/.ut2004/   #careful with this one, makes sure it is typed in EXACTLY, or even safer just delete ~/.ut2004 in nautilus
```

---

### Post by coarse.sand on 2007-06-17
Perfect fix. ut2004.ini and User.ini were created and settings are being saved when I exit now.

Just because I'm still learning Linux (switched about a month ago now) and it would be nice to know these things: I get the chown parts because I originally tried that when I first used gksudo nautilus to relocate my ut2004 folder instead of reinstalling, and 'apply permissions to sub folders' wouldn't work, but what might be in ~/.ut2004 that's causing the problem? I also don't know what chmod 755 does. Thanks again for the fix though. :D

---

### Post by aidanr on 2007-06-17
~/.ut2004 is where the per user configurations are held, say you were to install system wide in /usr then each user on the machine would have his/her configs for ut2004 stored in ~/.ut2004

755 is the permissions 

4 = read
2 = write
1 = execute

owner = 4 + 2 + 1 = 7
group = 4 + 0 + 1 = 5
others = 4 + 0 + 1 = 5

[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

---

### Post by coarse.sand on 2007-06-17
Aha, now I finally understand chmod 777. Thanks for that!

---

