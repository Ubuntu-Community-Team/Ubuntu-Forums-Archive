---
title: "Problem with Chess (glChess) with Natty"
date: 2011-07-06
forum: Desktop Environments
---

### Post by cybrsaylr on 2011-07-06
I like to play chess and was trying out Chess version 1:2.32.1-0ubuntu5 (glchess). It's nice and seemed to run fine. Well after awhile I noticed a strange electronic smell. I checked out System Monitor > Resources, to find one of the PC's cores was pegged out at 100%! 

I shut down GLChess and the pegged core went back to normal.
Started up GLChess again and the PC core pegged out to 100% straightaway! Did this a couple more times for confirmation and a core will peg to 100% every time glChess is opened! 

Had this same problem with pyChess on an earlier Ubuntu version than Natty, forgot which one. Just thought of passing this info on. Not sure if it is    bug with glChess, or perhaps glChess doesn't play nice with my PC.

I removed glChess.

---

### Post by gmargo on 2011-07-06
If any user application software can cause your CPU to overheat, then you have a hardware problem, not a software problem.

You should expect _any_ chess program to max out the CPU.  Why shouldn't it?  It gets to "think" while waiting for the slow human to move.

Update: I played glchess for a bit.. while I am a very poor chess player, the program did not seem to overtax itself to beat me.  Perhaps different backends?  I had no other chess programs installed.

---

### Post by John-B on 2011-07-06
cybrsaylr, were you beating the computer? :lol:
I just checked using system monitor and when playing it jumps just for a second to about 45-70 (probably less) to make the move and then drops to 0% cpu

---

### Post by cybrsaylr on 2011-07-06
I had no idea what is causing it to peg a core at 100% and it only happens when playing Chess. Usually opening a new app or program causes a momentary jump like you noted but this chess game causes it to go up and remain at 100% until I close the chess game.

---

### Post by cybrsaylr on 2011-07-06
Trying to remove double posting.

---

### Post by cybrsaylr on 2011-07-06
> **gmargo said:**
> If any user application software can cause your CPU to overheat, then you have a hardware problem, not a software problem.

Looks like this is the case.

Just installed glChess on my Toshiba laptop and all appears go run normal with no pegged cores for the few minutes it was tested.

What's strange is this looks like this exact same chess game I used on Karmic for two years with no issues at all but on Natty one of the cores stays pegged at 100%! 

I have no idea what the cause is for this?

---

### Post by wildmanne39 on 2011-07-06
Hi, is looks like a problem with the program, there has been several instances where a program has done that in natty but many different ones not anyone in particular. It s best to uninttall it and use another in its place if possible.

---

### Post by cybrsaylr on 2011-07-07
Thanks for the clarification.

Like I said the first time I ran into this bug of a core pegging at 100% was awhile back with Karmic when using pyChess. PC became sluggish, then there was that weird over heating smell. As soon as pychess was closed everything returned back to normal. So when I smelled that smell again I checked System Monitor and found a core pegged at 100% again with glChess this time. I removed those chess games. 

Tried a few other chess games and so far everyone is not running very well with Natty while they ran OK with Karmic. Hard to say what is causing this, Natty or Unity or the games themselves.

---

