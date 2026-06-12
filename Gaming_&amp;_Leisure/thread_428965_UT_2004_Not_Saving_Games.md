---
title: "UT 2004 Not Saving Games"
date: 2007-04-30
forum: Gaming &amp; Leisure
---

### Post by BlueStreak on 2007-04-30
I installed UT 2004 natively in Feisty.  Was fine for the first few rounds now it is no longer saving my game.  I finish a match, exit the game and when I go to play again I always start at the same place.  I reinstalled the whole game (haven't quite escaped what all those years of troubleshooting windows problems has done to me) and it didn't help.  Any ideas?  Thanks!

BTW, i exit by selecting the exit game option and there are no errors produced

---

### Post by Perfect Storm on 2007-05-01
Sounds like permission troubles. Have you at any times ran UT2004 as sudo? If so you possible messed up the permission of ~/.ut2004

---

### Post by BlueStreak on 2007-05-01
I've never run it as sudo but a permissions problem sounds likely.  I'm at work now so can't see what .ut2004 is currently set to but what should it be set to?  I know to use chmod but not sure what to set it to.

---

### Post by Perfect Storm on 2007-05-01
```
cd
sudo chown -R <username>:<username> .ut2004/
```

---

### Post by BlueStreak on 2007-05-01
Thank you, i tried the above but still doesn't work.

Here's what I see when I do ls -la in my home directory.

```
drwxrwxrwx  5 root mike     4096 2007-04-29 21:37 .ut2004

```

That tell you anything?

---

