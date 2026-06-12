---
title: "Are there any good contract bridge games in linux?"
date: 2007-03-05
forum: Gaming &amp; Leisure
---

### Post by jcpeart on 2007-03-05
I am new to linux and am really enjoying the experience.  I have noticed that there are many good games available.  But I have not found much in the line of contract bridge and that is what i really enjoy on the computer.  Are there any?

Thanks

Jim

---

### Post by avihappy on 2007-05-10
> **jcpeart said:**
> I am new to linux and am really enjoying the experience.  I have noticed that there are many good games available.  But I have not found much in the line of contract bridge and that is what i really enjoy on the computer.  Are there any?

Thanks

Jim

I want to know this too. Anyone?

---

### Post by _sluimers_ on 2007-11-10
All I've found is XContractbridge and GIB.

But GIB costs money -> [http://www.gibware.com/](http://www.gibware.com/)

This [review]("http://www.jimloy.com/bridge/review.htm") says GIB's the best though.

---

### Post by explainer on 2007-12-03
From what I can see of the GIB site, this is not a Linux program.  There really is no discussion of platforms, except for a reference to Microsoft...

---

### Post by nlz on 2008-02-01
Xcontractbridge is also not freeware. There is also Pybridge, but you can online play it online. I'm also desperately looking for a good (offline) bridge game for Linux.

---

### Post by nlz on 2008-02-01
you can also try to install GGZcards through Synaptic, the GGZ gtk+ package. It's got an bridge game in it, although the AI is not the best you could imagine.

---

### Post by rumfoord on 2008-03-20
I've just found Floater via another forum site (through Google). It appears to be server based only so no AI, which is a shame as I really  need to improve my bidding! On the plus side, it is open source and cross-platform.
You could give it a go, and ask there and you may get a more definitive answer!
You can install it using apt-get install floater, and check their website at [www.floater.org](www.floater.org)
If you find anything more, please let me know. I'm new to linux myself!
Regards,
R

---

### Post by kmicic on 2008-04-05
You may want to check out [gnubridge.org]("http://gnubridge.org") . It's not exactly a challenging bridge program yet, but I just about wrapped it up to where it's ready for somebody to start poking holes at it.

---

### Post by nlz on 2008-04-08
> **kmicic said:**
> You may want to check out [gnubridge.org]("http://gnubridge.org") . It's not exactly a challenging bridge program yet, but I just about wrapped it up to where it's ready for somebody to start poking holes at it.

Wow, great work! I will be your #1 tester ;) downloading now..

---

### Post by nlz on 2008-04-08
hmmmmm. what should I do? 

```
qnuf@mediaction:~/Desktop$ ls -a
.   gnubridge-0.1.1.jar  Link to Documents  structure.pdf   weblog 3~
..  Kaylois~             RESUME4+.doc       training mail~
qnuf@mediaction:~/Desktop$ % java -jar gnubridge-0.1.1.jar 
bash: fg: %: no such job
qnuf@mediaction:~/Desktop$ 
```

---

### Post by kmicic on 2008-04-11
% is a convention for a shell prompt. Do not include it in the command you are running.

---

### Post by nlz on 2008-04-21
I'm very sory kmimic, that was stupid of me.
We are very much enjoying the bridge game. The difficulty level could be a bit higher. The AI makes some weird decisions sometimes. For instance yesterday i played an ace of spades and then the AI threw an king of spades. The next round it became clear he also had the eight of spades, so it would be much more logical if he played that one.
It would also be great if you can start a new game automatically after your finished and if you could watch back in the game.

but overall: GREAT WORK!!!

PS If you are not looking for a test report, please say so and consider everything said here unsaid.

---

### Post by kmicic on 2008-04-22
At least it didn't throw an off color Ace at you, like it did at me another day. Search is capped at 2 tricks. If all plays are equal (ie the computer figures out it cannot take a trick in that frame), it'll play the first move in the list... Not very smart. I'll see what I can do about it in the next releases. Thanks for the feedback.

---

### Post by sideburns on 2008-05-03
> **kmicic said:**
> You may want to check out [gnubridge.org]("http://gnubridge.org").

I downloaded it, tried it and it worked.  Then, (I'm on Fedora, BTW.) I moved it to ~/bin because that seemed like the logical place for it and added it to my main menu.  For some weird reason, java couldn't find it unless I gave the complete path name.

Then, once I got it to start, it would hang before West played his first card.  I even tried running it from a terminal and got the same result.  And yet, before I'd moved it, it worked.  Weird!  Any ideas?

---

### Post by kmicic on 2008-05-04
These are unrelated problems. 

The seemingly "hanging" is just the program thinking about a move, and my lack of putting a code to indicate that. Some situations seem more complex to the computer than others, and so it may think longer on a move than usual. I try to streamline it to not take more than 3 minutes per move and less than 30 seconds on average, but it's currently not a garantee (I'll put in code in future releases).

The bin directory is for shell executables. In case of the command you are entering to run gnubridge, shell executable is the "java" interpreter itself. The name of the jar is a parameter to the java executable and does not follow the same rules when it comes to finding it in the PATH. Java offers you the option of putting the directory of your jars in the CLASSPATH env variable which works similarly to PATH for executables, but your better bet is to just make yourself a one-line shell script like 

#!/usr/bin/sh
java -jar [path to gnubridge]

and then stick that script in your bin directory.

I have just set up a mailing list to handle questions about gnubridge to keep from thrashing this thread. You can sign up for it from the [http://gnubridge.org](http://gnubridge.org) page.

---

### Post by sideburns on 2008-05-04
> **kmicic said:**
> These are unrelated problems. 

The seemingly "hanging" is just the program thinking about a move, and my lack of putting a code to indicate that. Some situations seem more complex to the computer than others, and so it may think longer on a move than usual. I try to streamline it to not take more than 3 minutes per move and less than 30 seconds on average, but it's currently not a garantee (I'll put in code in future releases).


Thank you.  I'll try again and be more patient.

> 
The bin directory is for shell executables.

Or, for anything else I feel like putting there.  I've been running Linux (dual boot with Windows) since about '98, and know what I'm doing.  If I feel like putting programs there so that they survive a reinstall (I have a separate /home partition) there's no reason I can't.  Thanx, however, for replying.  I'm thinking about putting a link to your program at fedoraforum.org, so that they can enjoy it too.

Later: I tried again.  It couldn't decide on an opening lead in 10 minutes on a 1.8Ghz machine.  My CPU monitor showed <10% activity.  I tried running top in a terminal and java was not one of the most active programs.  (If it showed at all, I didn't spot it.)  It was just sitting there, doing nothing.  I can not in good conscience recommend this program until and unless it works.

---

### Post by hendersoneg on 2009-03-06
I too am a bridge fanatic.  I have yet to find a really good program than runs under linux but what I have done is installed XP into virtual box and run my old Bridge Baron that way.  Seems to work just fine, but you do have to have windows, ugh!!

---

### Post by jonthysell on 2009-03-06
Try EasyBridge: [http://www.boardgamegeek.com/file/info/13285](http://www.boardgamegeek.com/file/info/13285)

It's old windows freeware, but it runs great under wine.

I can't really judge how powerful the AI is (I'm a beginner so I lose anyway), but it does let you set options for everything (bidding conventions, house rules, etc) and it can give you bidding and play tips with explanations.

---

### Post by themacmeister on 2009-03-10
Speaking of Wine, I use Hoyles Card Games 2001 under Wine, and it works perfectly. You may need to experiment with wine versions to get fullscreen working correctly, but ever since 0.99.4 fullscreen works. It is a commercial game, but you could discover it on a torrent or rapidsh*re site. It is only 24MB compressed. I own HCG 2009, and it weighed in at 700+MB, and is almost unusable. I'll stick with 2001 thank you!

---

### Post by leden on 2009-11-26
Try "MVP Bridge" - it works without any problem under Wine.
It's not free but you have a fully functional trial (maybe it will last forever on linux :)).

> 
Acknowledged as the best shareware Bridge game available, MVP Bridge includes advanced artificial intelligence for better bidding and play, Internet multiplayer support, a tutorial for Bridge beginners, 13 conventions, and an excellent user interface. See why MVP Bridge is the only shareware game ever nominated two years in a row by Computer Gaming World for its industry awards.


If you just wanna play online with other human players or friends, I suggest [www.bridgebase.com](www.bridgebase.com) it's one of the most popular free bridge online sites with an average of over 10000 players online all the time.

---

### Post by JohnBUK on 2011-01-12
Can confirm MVPBridge does run satisfactorily under Wine. Have Ubuntu 10.10 and Wine. Also it seems a very good Bridge game for reasonable players.

---

