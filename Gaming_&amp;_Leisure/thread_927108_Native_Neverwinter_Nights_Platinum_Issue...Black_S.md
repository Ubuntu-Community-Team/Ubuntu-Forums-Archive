---
title: "Native Neverwinter Nights Platinum Issue...Black Screen."
date: 2008-09-22
forum: Gaming &amp; Leisure
---

### Post by dayosh on 2008-09-22
Greetings, everyone.  :)

After meticulously following the tutorial I found [_here_]("http://ubuntuforums.org/showthread.php?t=113259"), I find that while the installation seems to have gone swimmingly, the actual running of the program seems flawed.

My difficulty is that upon running the program, I am met with a black screen.  No text, no images or pictures (like the NWN logo or anything like that).  Nothing.  Just pitch blackness.  I would like to see if there is an error occuring somewhere, but I am unable to exit out of the window (tried alt-tabbing, ESC-ing, even Alt-F4-ing, and nothing seems to work).

If anyone has any suggestions, or has any other means one could exit out of a full-screen program (like NWN), it would be greatly appreciated.  Thanks very much in advance!  :)

---

### Post by dayosh on 2008-09-23
...Anyone?

---

### Post by Perfect Storm on 2008-09-23
More info is needed...

Video card?
Are you sure follow it word by word?
Did you try installing so movies can be played? This might also be an issue, never could it get to work.

---

### Post by dayosh on 2008-09-23
Video Card would be an Nvidia 8800 GTS, pretty much brand new (installed it after having gaming difficulties with my former ATI card).  Has worked like a gem so far.

Followed it word by word, aye.  And yes, I did install it so movies could be played.  I had initially installed it with just the core pack (no expansions) that did not have movie support.  I had decided to reinstall it and try to do the movie support after that (really like cut-scenes, and whatnot).

Any other info that might be helpful just ask, and I will provide as much as possible.   Thanks again, AI!   :)

---

### Post by Perfect Storm on 2008-09-23
Try check nwn error logs, eventually a terminal output would be nice.
What about compiz try disable it. It's known to be a game-killer ;)


Last resort I made this; [http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn) (ignore installing the 32bit libs if you're using 32-bit).

---

### Post by dayosh on 2008-09-23
Hrm...tried checking the error logs ("nwn/logs/nwclientError1.txt") and the other one ("nwn/logs/nwEventLog1.txt").  Both are coming up completely empty.  However, I did notice something at the bottom of "nwn/nwmovies.log".

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

Unsure if that's relevant or not, but figured I'd throw it in, just in case.  Tried the Compiz thing "metacity --replace", but it still gives the same result.

Maybe I'll just try ripping everything out and trying your tutorial.  I'll give it a shot either this evening or tomorrow, and post if the results are any different or similar.

Also, with your tutorial, does this include movies, or movie-less?

Thanks again, AI.  Mucho appreciated!   :D

---

### Post by Perfect Storm on 2008-09-24
It's movie-less, never could get it working on my computer.

---

