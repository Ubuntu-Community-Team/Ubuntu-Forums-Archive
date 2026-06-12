---
title: "Alien Arena crashing loading level 5"
date: 2009-11-22
forum: Gaming &amp; Leisure
---

### Post by Man with Hat on 2009-11-22
I found a similar thread to this dated over a year ago saying that they had crashed constantly on loading level 3. The fix for it makes no sense to me as I am still relatively new to linux. I'd happily alter the line in Terminal as suggested, if I knew where to find its source or what SVN is. Also I don't know if this will fix my issue as this was for the last version of Alien Arena. Could someone please give me some noobier instructions that would work?      ](*,)

---

### Post by Irritant on 2009-11-22
That bug was fixed ages ago, what version of Alien Arena are you running?

---

### Post by Man with Hat on 2009-11-23
Not sure, I've migrated from windows recently so I'm kinda used to seeing "help-> about" or right click its file -> properties to see things like that. I only downloaded Alien Arena a couple of days ago using Karmic Koala's "Ubuntu Software Centre" I assumed it was the latest. I'm not familiar with the update process either. I went into the update manager and it seems happy with my system.

---

### Post by Man with Hat on 2009-11-23
Oh wait, I found v7 in the background of the credits (assuming version 7?)

---

### Post by Irritant on 2009-11-23
Just drop the console, and in the bottom right, the version number is displayed.

---

### Post by Man with Hat on 2009-11-23
yep, version 7

---

### Post by Irritant on 2009-11-23
7.0?  That's a pretty old version.  What is the name of the map that is crashing?

---

### Post by Man with Hat on 2009-11-23
> **Irritant said:**
> 7.0?  That's a pretty old version.  What is the name of the map that is crashing?

Old version? I wonder why it downloads an old version out of software centre........
Is there an easy way to update/upgrade it?

sudo apt-get upgrade just got me a bunch of gstreamer updates. 

I don't know the exact name of the map as it says its loading and crashes in less than a second. Its EURO2..... something or other. Its the 5th map though. Of that I am certain

---

### Post by Irritant on 2009-11-23
[http://gwos.org/doku.php/guides:64bit:alien_arena](http://gwos.org/doku.php/guides:64bit:alien_arena) 

I think these instructions will work for 32 bit as well.  

This gets you the latest SVN of the game, which while at times can be unstable is the best way to stay current with the game.

---

### Post by Man with Hat on 2009-11-23
Thanks for the guide,

I gave it a try but now the game won't even launch. I didn't remove the original version I had on there though. I'll give that a try and let you know how it goes.

Also if this ends up working, will that mean it will auto update through update manager or apt-get update?

---

### Post by Man with Hat on 2009-12-18
Finally got some time to try this again. Ok I have uninstalled AA and then followed the instructions that you linked me too. When I use the commands:
cd .. && cp -r * ~/.Games/AlienArena

Everything that it tries to do is "permission denied" I have tried this using sudo command as well and get the same result. Incidentally I don't have the necessary game files to run now!!
Any ideas?

---

