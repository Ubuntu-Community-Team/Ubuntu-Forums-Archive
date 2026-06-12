---
title: "ok, now im clueless..."
date: 2009-09-16
forum: Gaming &amp; Leisure
---

### Post by Kyle.Gant on 2009-09-16
after a lot of time with someone else helping me with this problem, i had my game working. i installed oblivion, direct x 9, and wine, and finally got the game running. i started a new game. the game was reacting slow, so i changed all of the video settings in it to low, and restarted. about 5 minutes into character creation, the game died. no error message, just one second i was making my character, next i was on my desktop, which had suddenly went from 1440x900 to 800x600. took me 5 minutes to get it back to the proper dimentions. i tried to restart oblivion and it immediatly gives me a error message and dies. can someone help me figure out what the heck is wrong...you know, again?

---

### Post by Bölvaður on 2009-09-16
The stickies on this subforum say that if you post WINE questions the post will be deleted, so I hope you will read this before a moderator does, as then this might be of a little use.


1. start the game from the terminal, often the best way is to copy the command from the launcher and just copy it into the terminal.
this should spew out some nice output saying what might be wrong, if you have the patience to read it through.

2. the game/wine changes the resolution settings so when it crashes it cannot change it back again.


it shouldnt take you that long time to get correct resolution back. if you have nvidia card then open terminal or Alt+F2 and type nvidia-settings

or gnome-display-properties which should redirect you into the correct program (if ati or what ever vendor you got your card from has it's own config program).

---

