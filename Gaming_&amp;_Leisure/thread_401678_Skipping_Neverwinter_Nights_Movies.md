---
title: "Skipping Neverwinter Nights Movies"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by gtmaneki on 2007-04-04
Hi, all.  Firstly, I'd like to thank everyone -- and particularly Leech -- for their discussions on how to get NWN up and running under Ubuntu.  I now have it running, and even have movies and sound going, although I do have one question still:

Is it possible to skip the movies?  I'm getting a little tired of having to watch the intro in particular every time I load the game.  (I know, it's a minor complaint, considering the game's actually working well otherwise.) :-({|= 

Here are my system particulars:
* Kubuntu 6.06
* Installed to /usr/local/games/nwn
* NWN version 1.68, installed from the original game CD + XP1 + XP2
* I am unable to skip the movies regardless of if I start the game from KDE, XFCE, or from a new X session

=================================

Down here I'll just post a list of links to the howtos that helped me get to this point, in case someone needing help installing the game runs across this post:

* [HOWTO: Installing Neverwinter Nights Platinum]("http://ubuntuforums.org/showthread.php?t=113259&highlight=neverwinter") (for movies)
* [NWN Linux Installer]("http://icculus.org/~ravage/nwn/")
* [NeverWinter Nights Sound Issues]("http://ubuntuforums.org/showthread.php?t=61511&highlight=neverwinter")
[HOW TO: Run games on a new X server]("http://ubuntuforums.org/showthread.php?t=51486")
* I also kept getting an error about not being able to locate /etc/X11/xserver/SecurityPolicy, so I copied over the file from  /usr/share/doc/examples .  I read about this somewhere on the forums, but can't find the post now.  Thanks to whomever provided the answer!
* To get the sound issues fixed, I had to copy the Ubuntu libSDL-1.2.so.0 file to /usr/local/games/nwn, and remove ./lib from the "path" line in the nwn file.
*[Xgame]("http://happypenguin.org/show?Xgame") is an easy way to get games to start on their own X server

---

### Post by blue_Sphere on 2007-04-05
Try going to the nwn.ini and adding this

[Display Options]
Disable Intro Movies=1

---

### Post by gtmaneki on 2007-04-05
Thanks!  That's a lot better than what I was doing before -- going to a virtual console terminal and manually killing BinkPlayer.

---

### Post by Ng Oon-Ee on 2008-08-07
I'm well aware this thread is from last year, but I've been searching around without any luck and thought I'd try here as well.

I've set NWN up according to the first thread listed above and have the movies working fine. Previously I was playing without NWMovies installed, and I could run in windowed mode just fine, when my mouse hit the edge of the NWN window it just crossed over to the desktop, allowing me to chat and play.

Currently, with NWMovies installed, the game still runs in a window but my mouse and keyboard are 'captured' by NWN, meaning for all intents and purposes the game is fullscreen, except I can see my toolbars and desktop around the edges.

Also, setting Disable Intro Movies=1 in the appropriate place has no effect for me. The movies play all the way through (irritatingly enough they're unskippable).

Any suggestions?

---

### Post by Ng Oon-Ee on 2008-08-09
Latest NWMovies release (NWMovies v4.0 RC1) fixes the problem of keyboard/mouse getting captured in windowed mode, but I still can auto-skip the movies. Any ideas out there?

Anyone interested can get this release from [this link.]("http://nwn.bioware.com/forums/viewtopic.html?topic=629464&forum=72&sp=0") Its not linked on the main website, probably because its RC and not full release.

---

### Post by DoktorSeven on 2008-08-09
Interesting how you go through the process of adding movies to Linux NWN then ask how to skip them... ;)

Really, did you try just disabling the NWN movie hack?

---

### Post by Ng Oon-Ee on 2008-08-10
You know, if you've read the thread starter's post, he mentions that he's trying to skip the INTRO movies, not all the movies, which is exactly what I'm asking about as well.

To further explain, there's like 5 (which is just nuts I think) movies which play at the start of NWN, before you get to the main menu. The last of these lasts for a good 2 minutes I think. Waiting for 3 minutes total just to start the game is pushing it, really.

But throughout the rest of the game (in particular between chapters) there's movies fleshing out what has been happening in-game, the reason for enabling movies is to watch those, NOT to watch the intro movies.

So, as stated above, normally those can be disabled by the appropriate line in the nwn.ini file, unfortunately for me that doesn't work.

---

### Post by ftek on 2008-09-02
Not intending to be a smart-*** here, but I just press escape. It seems to work fine.

---

### Post by Ng Oon-Ee on 2008-09-02
Yes, escape works, now.

Previously it didn't. I'm not even sure what I did to get it to work, I've been messing around with nwn.ini, nwmovies.pl, and all that for ages and can't remember what I've done.

Basically, in the end I just deleted those specific movies (the intro ones). Stopgap solution, but it works, and I get to play (which is the whole point anyway) without waiting for some insane amount of time.

Thanks for your contribution, ftek :)

---

