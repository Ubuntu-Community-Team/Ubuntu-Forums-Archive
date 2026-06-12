---
title: "Has anyone got Mame to save high scores after exiting a game?"
date: 2010-06-04
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2010-06-04
Hi.
Has anyone got Mame to save high scores after you exit a game?
I notice that when I get a high score and then enter my name, when I close the game and later start the same game again, the high score is gone. I use GMAMEUI with SDLMAME. :confused:

---

### Post by Carbs70 on 2011-04-21
I've got the same issue myself. I still haven't managed to get it working...however I did find this resource:

[http://highscore.mameworld.info/](http://highscore.mameworld.info/)

Downloaded the file....not sure if it's for windows only or ubuntu....but I extracted into my /usr/games dir, created a "hi" folder, and changed permissions and things, and set the support file preferences thing to point to it.... no joy.

Also stuck the file/folder in the same folder as my ROMs... no joy there either..

If anyone has a breakthrough, I'd really appreciate  the help.

---

### Post by Carbs70 on 2011-05-01
From Nicola himself on the Mame website...so I guess the answer is "can't happen in the more recent versions of MAME"

> **Why doesn't my favorite game save my high scores?**

 Almost all of the games that actually saved the high scores in the  arcades have the high score saving supported in MAME. However, quite a  few games — especially the classics from the late 70's and early 80's —  did not have any mechanism to save high scores. When the power plug was  pulled on these games, the high scores were lost. This generally wasn't a  big problem in the arcades, as they tended to leave the games up and  running for long periods of time. 
Unfortunately, when you play a game in MAME, it is as if you are  turning the game's power on fresh, and thus all of your high scores will  be missing unless the original game had support for saving the scores.  Early versions of MAME had a built-in hack that would attempt to save  high scores even in these older games, but the hacks were eventually  deemed to be too problematic for accurate emulation, and this support  was removed. 
One alternative to saving high scores is to make use of MAME's  "autosave" functionality. If you run MAME with the -autosave parameter,  then when you exit the game, MAME will save the state of the emulation,  and will attempt to restore that state the next time you start up MAME.  To the game, it's as if you never pulled the power cord. At this time,  however, only a subset of MAME's games fully support save states, so  this approach is not a perfect solution. 
Note that some games (like many Atari games) keep only the top  three high scores; lower scores are deleted. This is faithful to the  original arcade games. 


---

