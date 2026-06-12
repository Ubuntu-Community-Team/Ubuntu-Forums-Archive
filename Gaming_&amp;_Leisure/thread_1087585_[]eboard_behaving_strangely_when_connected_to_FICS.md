---
title: "[]eboard behaving strangely when connected to FICS"
date: 2009-03-05
forum: Gaming &amp; Leisure
---

### Post by mr.nope on 2009-03-05
I've been using JIN, the Java applet provided by freechess.org to play until the site went down a few days ago. Fortunately the problem only seems to affect the web server, the actual chess server (FICS) is still available.

I've been trying some of the FICS-compatible programs (xboard, pychess, eboard). I like PyChess a lot, but it's terribly unstable and xboard isn't very intuitive imho. This leaves eboard.

However, whenever I connect eboard to FICS, every new game started on the server is automatically displayed, resulting in the program being unusable. For instance, if I try to have a look at the "seek graph", the view immediately jumps back to the board and starts observing the newest game and then keeps jumping to every new game... 

Does anyone know how to change this? Probably some trivial setting, but I really can't figure it out.

---

### Post by pwc on 2009-03-07
OK, I remember this happening to me a couple of years ago, it is a simple fix if I can just remember! I really haven't played much since then so all this is memory and I am 69 years old. 

I believe if you previously had used BabasChess with Windows before using Eboard, it would change a varience(I'm not sure this is the right word) on FICS web site. Changing that varience back would fix the problem.

If you can't figure it out from this info, post back and we'll dig further.

pwc

---

### Post by mr.nope on 2009-03-12
Thanks for the quick reply. I don't think I ever used BabasChess, but maybe some other client made these changes. 

After playing around with the variables in I got this, which works:

```
Variable settings of *:

time=2       private=0     shout=0         pin=0           style=12 
inc=12       jprivate=0    [COLOR="Red"]cshout=0  [/COLOR]      notifiedby=1    flip=0
rated=1                    kibitz=0        availinfo=1     highlight=0
open=1       automail=0    kiblevel=0      availmin=0      bell=0
             pgn=0         tell=1          availmax=0      width=79 
bugopen=0                  ctell=1         gin=0           height=240
             mailmess=0                    seek=0          ptime=0
tourney=0    messreply=0   [COLOR="Red"]chanoff=1 [/COLOR]      showownseek=0   tzone=SERVER
provshow=0                 silence=0                       Lang=English
autoflag=1   unobserve=1   echo=1          examine=0
minmovetime=1              tolerance=5     noescape=0      notakeback=0
```

I haven't a clue what exactly I changed... just perhaps some of the two settings highlighted.

---

### Post by pwc on 2009-03-12
Good for you, tracking it down. Neither one of those variences ring a bell, but it has been over a couple of years. I'm setting up Eboard again, maybe I'll see you on FICS one day. 

Have you installed timeseal yet, I just downloaded it  and not exactly sure how to set it up. Directions are not real clear, though I have done it before.

pwc

---

### Post by musings on 2009-10-10
For the sake of the archives, BabasChess does indeed alter some variables that cause strange behaviour in eboard. On the eboard website under bugs, it says 'FICS/General: FICS shows a line for each player that logs in/out and for each game that ends, driving you nuts: you probably connected to FICS with Babaschess and it messed with your variables. Just type set pin 0 and set gin 0 and you're back to normal.'

Regards, Gary

---

### Post by rigao on 2009-10-10
When you have ubuntu 9.10 installed, it will come with xboard 4.4.0 which is far better thant the actual version in the repositories (you can also download a debian package from [http://www.open-aurec.com/wbforum/WinBoard/xboard_4.4.0~hgm-8_i386.deb](http://www.open-aurec.com/wbforum/WinBoard/xboard_4.4.0~hgm-8_i386.deb) but given that you just need to wait 15 days to have the new ubuntu, i don't know if it is worth the effort). It has its things, like to play a game, you need to always write the command (seek 3 0 etc etc) which is kind of annoying (same for resigning).

On the upper hand, this is a GUI which is actually being improved, so any day you will find that they have solved this issues. So if you are more interested, just ask, I will be glad to help you with it,

About timeseal, I copied it to /usr/games/ and it just works, but in xboard, I don't use eboard, so I can't help you at all.

---

### Post by mr.nope on 2009-10-10
I must admit that I eventually gave up on the various native clients and now use BabasChess. Works just fine in wine.

---

### Post by rigao on 2009-10-10
When I tried to use babaschess through wine, i had problems with timeseal. I was loosing on time too often just because it were not using it (so it seemed).

And xboard let me use Rybka 64 bits just fine, I don't have to do much to have it working properly. This is why i went for xboard over jin or babaschess, and i'm quite happy with it.

---

### Post by kewlbns69 on 2010-01-10
i tried babaschess myself today (used on windows before). it wouldn't run. does anybody know how to get eboard running with timeseal though? i'm losing my mind over here

p.s running ubuntu 9.10 x64

---

### Post by elsdyr on 2010-10-04
I have exactly this problem after I tried out pychess. Writing the following in the cmd line
```
cshout 0
chanoff 1
```doesn't help.

Your help is appriciated :)

---

### Post by mr.nope on 2010-10-04
try the following:
```
set pin 0
set gin 0
```

All the help files for the various variables are here: [http://www.freechess.org/Help/HelpFiles/manual_vars.html](http://www.freechess.org/Help/HelpFiles/manual_vars.html)

---

### Post by elsdyr on 2010-10-07
So I've read your posts more carefully, and it all seemed to work. I'll leave this for (my) future reference:
```
set pin 1;set gin 0;set availinfo 0;
```

It can be useful to create a shortcut in the shortcut pane of eboard to issues these commmands in on click, making it comfortable to switch between eboard and Pychess.

Thanks

---

