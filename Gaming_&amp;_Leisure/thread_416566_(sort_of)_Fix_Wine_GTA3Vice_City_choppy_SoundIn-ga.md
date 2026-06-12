---
title: "(sort of) Fix: Wine GTA3/Vice City choppy Sound/In-game videos"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by chiefwhosm on 2007-04-21
Hi,
Posted this ages ago on the wine mailing list, and I was thinking that maybe I should post it here too for those who still play the game(s) under linux.
Now these are tests I did a while back, on an old version of wine, so some bugs I encountered may be fixed now, also if these don't work for you then all we can do is hope for a new wine version with more fixes :)

Grand Theft Auto 3:

Problem: Choppy sound (so bad you can hardly work out what people are saying), radio stations dont work either. In-Game videos are slow.

Solution: Enable Trails in the graphics options, sound then works perfectly, as do the movies.

Downside 1: FPS hit, your game may become a snails pace depending on your system specs (I was using a 6800GT at the time of testing, and it managed okay).

Downside 2: Ghostly images. (I hope this wont happen because the version I used was from a few years back, and there have been so many d3d enhancments now) the image is duplicated, one flipped horizontally on top of itself.

Grand Theft Auto - Vice City:

Problem: Choppy sound (so bad you can hardly work out what people are saying), radio stations dont work either. In-Game videos are slow. With newer wine versions I also get black cars now.

Solution: Now I never got this to work, I think it needs someone with more wine experience than I have (I dablle in linux but usually return to windows a few days later) but there's a custom dll for vice city, which allows the user to configure special graphics options using a configuration file, one of these options are trails.

The files can be found over at gtaforums:
[url]http://www.gtaforums.com/index.php?showtopic=186404&st=0[/ur]

Also some of the other options might fix the black cars, but as I said, I could never get wine to use the dll file to start the game with under linux, so I didn't get too far.

Well maybe that will help someone who is suffering from problems, at any rate if someone new to linux does try to play one of the games, least this thread may offer help if they get the truly terrible sound problem that I always got (who'd have guessed editing a graphics option would fix sound :) ).

If none of these things work for you, then I guess just wait on the new wine versions to be released and hope the audio improvments about to take place will help it (and other games).

---

