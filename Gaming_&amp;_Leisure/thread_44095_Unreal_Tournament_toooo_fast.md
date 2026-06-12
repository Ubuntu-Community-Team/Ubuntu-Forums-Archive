---
title: "Unreal Tournament toooo fast"
date: 2005-06-24
forum: Gaming &amp; Leisure
---

### Post by cancech on 2005-06-24
Hi,

I tried to get Unreal Tournament and the UT2003 demo working but I'm stuck. I got all both of them installed and they "work", but the thing is that they're not running properly. UT and UT2003 run waaay tooo fast. Both run at about twice as fast as they should. In UT if I set the game speed to 50-60%, then it seems to be fine. I had this problem before when I was running Windows and messing around with the power options got rid of this increase in speed. I was thinking that doing the same in Ununtu could fix the problem, but I've no idea where to even start looking for power settings.

You'll probably need to know some system specs, so here they are:

Model: Dell Latitude D600
Video: ATI 9000 32 MB 
RAM:   512 MB

For the video card I'm using the default drivers that came with Ubuntu.

I'll try installing some other games to check if it's a UT issue or if it affects more things.

On a side note, I am running Warcraft 3 through cedega without any problems.

Any ideas what could be causing the increase in speed?

---

### Post by cancech on 2005-06-24
I installed Supertux and TuxRacer and both of the run fine, so the speed issue is probably just an Unreal Tournament problem.

---

### Post by bored2k on 2005-06-24
[QUOTE=cancech]I installed Supertux and TuxRacer and both of the run fine, so the speed issue is probably just an Unreal Tournament problem.[/QUOTE]
 Can't you load the higher settings possible so the game lags a bit, thus being slower but better looking ? I wish my problem was a super fast speed on my unreal 2004 .. still, it rocks !

---

### Post by tread on 2005-06-24
In Unreal Tournament you can set the game speed when you start a game, that is prolly whats messed up. Try reducing that.

Edited to add:
Shucks, I broke the 666 posts label  O:)

---

### Post by cancech on 2005-06-24
I don't think that it has anything to do with the system running the game "too well" but with the game speed being set too high. I tried changing the resolution from 800x600 to 1024x768 and the game speed didn't decrease, but framerate did. For example the shockrifle shoots at a rate of ~3 rounds per second, but the game itself lags. Even running the game at 800x600, then it slows down when there is too much scenary or if there is too much happening on screen.   :-?

---

### Post by cancech on 2005-06-24
[QUOTE=bored2k]Can't you load the higher settings possible so the game lags a bit, thus being slower but better looking ? I wish my problem was a super fast speed on my unreal 2004 .. still, it rocks ![/QUOTE]

You can do that in UT, but I didn't see an option for it in UT2003_demo, I'll take another look, but I'm pretty sure that option isn't there.

Besides, the game speed was set to 100%, why would it behave like it was at 180-200%?

---

### Post by rhino on 2005-07-04
[QUOTE=cancech]You can do that in UT, but I didn't see an option for it in UT2003_demo, I'll take another look, but I'm pretty sure that option isn't there.

Besides, the game speed was set to 100%, why would it behave like it was at 180-200%?[/QUOTE]
 I have the same problem, From my google hunting the problem seems to be that the speed-step function of the processor makes the game think one thing while actually being another.  I went so far as to diddle powernowd so that if im plugged im running at full speed. I then reinstalled the game, but yet that does not seem to help. If any one has a soultion it would be glad to hear it

---

### Post by rhino on 2005-07-05
well i did some more googling and came up with a solution. Some what sloppy but it works. If any one has a better idea im open to it. That being said here goes...

Make sure and back up all files before making any chhanges.


go to you installation directory (by default /usr/local/games/ut/) and use your editory of choice to create this file.

```
#!/bin/sh

( while true; do true; done ) &
sleep $1
killall busy
```

second edit you ut file in the same directory  adding the following lines

```
busy 4 &
sleep 1
```

some where between the #!/bin/sh and the UT_PREFS="${HOME}/.loki/ut" lines

at this point and time make sure you execute permissions on the created busy.sh file.


create a symlink named busy in /usr/local/bin pointing to the busy.sh file.

```
cd /usr/local/bin
sudo ln -s /usr/local/games/ut/busy.sh busy
```

 You now should be able to type ut from console as normal except you will note it running at the normal speed. This basically taxes the processor for a short interval which allows UT to read the correct spead.

I hope this has helped.

---

### Post by Chal on 2005-12-15
try 

sudo killall powernowd

before starting the game

hope it works for you

CHAL

---

### Post by Leigh on 2006-01-14
I found a possible fix to this problem, unfortunately I can't get it to work but that's probably due to my incompetence. Here's the link ( [http://www.icculus.org/lgfaq/#runeutfast](http://www.icculus.org/lgfaq/#runeutfast) )

---

### Post by RickKnight on 2006-01-25
[QUOTE=cancech]Hi,

I tried to get Unreal Tournament and the UT2003 demo working but I'm stuck. I got all both of them installed and they "work", but the thing is that they're not running properly. UT and UT2003 run waaay tooo fast. Both run at about twice as fast as they should. In UT if I set the game speed to 50-60%, then it seems to be fine. I had this problem before when I was running Windows and messing around with the power options got rid of this increase in speed. I was thinking that doing the same in Ununtu could fix the problem, but I've no idea where to even start looking for power settings.

You'll probably need to know some system specs, so here they are:

Model: Dell Latitude D600
Video: ATI 9000 32 MB 
RAM:   512 MB

For the video card I'm using the default drivers that came with Ubuntu.

I'll try installing some other games to check if it's a UT issue or if it affects more things.

On a side note, I am running Warcraft 3 through cedega without any problems.

Any ideas what could be causing the increase in speed?[/QUOTE]
Cancech,

How do you set the games speed in UnrealTournament?

Thanks,
CatDadRick

---

### Post by RickKnight on 2006-01-25
[QUOTE=Leigh]I found a possible fix to this problem, unfortunately I can't get it to work but that's probably due to my incompetence. Here's the link ( [http://www.icculus.org/lgfaq/#runeutfast](http://www.icculus.org/lgfaq/#runeutfast) )[/QUOTE]
I have this fix. For the most part it works, but after I applied it, I had no sound from UT. That problem has corrected itself and I now have sound back and a playable UT.

To apply the fix, save this [link]("http://icculus.org/lgfaq/files/ut") to your system somewhere and then copy it to your UT game directory, usually /usr/local/games/ut. Change permissions to root.root and set the mode to 755.

---

### Post by DarkED on 2006-03-05
You must run it with the command line parameter '-cpuspeed 2500' without the asterisks and where 2500 is the speed of your processor.

This is how you do it in Windows, and that's how the engine is coded. Any problems, just ask :D Good luck!

---

### Post by lH)4~mK0e on 2006-07-17
That doesn't seem to work either.  The sleep method is like a post caching method and makes the play real choppy and not smooth at all.

---

