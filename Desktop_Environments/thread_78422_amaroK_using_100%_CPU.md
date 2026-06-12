---
title: "amaroK using 100% CPU???"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Sophisto on 2005-10-18
I thought I could just add this in case someone else had the same problems, since after a look around I found that turning off the "last.fm" supports like "retrive similar artists" resolved the problem. Now the CPU use is down to 5-10%.

Hi! 

For some reason when playing a song in amaroK (in gnome, using xine) my CPU usage goes up to 100% and obviously other applications start to go a bit slow due to this. I have also tried with Gstreamer without any result. Also when playing song I can see the mouse icon change to one with the arrow and a "clock" next to it and iv im not wrong thats the one that comes up when amarok is loading something which, to my knowledge it isn't! 

Any suggestions?

Semifixed -> when changing the view from "current" to "home" the CPU usage goes back to normal....

---

### Post by magnusbb on 2005-10-18
Thanks for the great tips!

---

### Post by skoal on 2005-10-18
Yeah, I couldn't figure out why my network was going crazy until I ran an ethereal sniff on it.  Sure enough, audioscrobbler (last.fm)...

By the way, I have a SB Live! card which can do hardware mixing on it's own.  The easiest way to kill (or keep) the artsd from popping up is: system settings > sound&multimedia > (uncheck) Enable the Sound System.

Some people have suggested 'kill -9 <artsd>' (or the like), but the method above keeps it from loading at all. 

\\//_

---

### Post by the_purulent on 2005-10-18
I have this issue as well and could not figure out why. Hopefully these tips help.

---

### Post by Sophisto on 2005-10-19
Skoal - Sorry to be so thick but exactly where is the "system settings > sound&multimedia" you were talking about? Cant seem to find it!

---

### Post by the_purulent on 2005-10-19
Worked like a charm for me. Turned of the find similar artists / info thing and wham! Perfect performance.

---

### Post by mattismyname on 2008-01-31
Mine's running at about 15% CPU on a 2.20 GHz P4.  More than I think a media player should.  Need to find a way to run vtune on it...

---

