---
title: "problems after upgrade to 9.04-no sound and tracker applet malfunction"
date: 2009-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsally on 2009-04-24
I upgraded to my dell inspiron from 8.10 and lost the sound.  How do I fix
this?  Also the tracker applet pops up a message "There was an error while
reindexing"  and I am unable to remove the little screen because none of
the buttons work on it.

---

### Post by celticchrys on 2009-04-24
I'm having the same problem on two different computers.  No clue why.

---

### Post by delirium85 on 2009-04-25
I have the same issue, only I had sound until I plugged headphones in, then there was no sound coming out of the speakers or my headphones.  Anyone, any ideas?

---

### Post by overandunder on 2009-04-25
+1 

I fixed the Tracker Applet problem (see Thread above), but not sure what's happened to the sound?

I get the usual Ubuntu 'drumroll' after log in (so I know the hardware is still ok), but If I go to an 'external' sound source via Firefox, e.g. You Tube, BBC i Player, etc nothing happens!! This worked fine before!

---

### Post by nobodie on 2009-04-26
Apparently the link the above poster wanted to show didn't come through so here is the simple way to get your tracker working:
in a terminal (or alt + F2 if you like to do that) 

$ tracker-processes -r

and that will reset tracker and solve that problem.

However, while my desktop had initial problems (fine at first then after @2 minutes degradation to comeplete garbage over about 1 minute usually) with sound and video playback for everything after updating to jaunty RC1. I fixed that by reinstalling everything (xine, gstreamer, vlc, and totem as well as multimedia codecs) but now my wife's lappie (Dell Inspiron 1520) had both the tracker problem (fixed as above) and has also lost all audio, even system sounds. 

Could someone who knows audio stuff in ubuntu step in and give a hand?

---

### Post by aikiwolfie on 2009-04-26
My M1330n has started producing a weird crackling sound when it gets to the desktop. The login sound plays fine. But videos are a different matter. I tried to play some flash videos I know work fine on other PCs and I can hardly hear anything. Turn the sound up and it sounds like crap.

I'm holding off the upgrade on my desktop until some of these issuse get sorted. Of course I'll have to make a Live USB disk and fix the xorg.conf file first since the new X server still has issues with dual graphics cards and refuses to choose a default.

Bad upgrade experiences push people away from Linux.

---

### Post by overandunder on 2009-04-26
FIXED

For the guys who have partial / some sound this is what I found;

As above I had the usual UBUNTU startup drums + system sounds, but nothing other than that.

Whilst looking around the net at various sound sources, YouTube, BBCi Player, etc (which weren't working) I realised that these all use Adobe Flash Player.

Out of interest, I went to Adobe's website and downloaded the latest Flash Player version (they have a .deb file for Ubuntu 8.04+, which is the one I chose to install).  After this I restarted my computer - and bingo ! back came the sound!!

Worth a try if nothing else?

---

### Post by tashammer on 2009-04-26
i appear  to have similar sound and tracker applets problems as described above, i.e. tracker applet loops, and no sound, not even the drums.

i did try reinstalling an earlier version of Adobe Flash (for Ubuntu 8.04) but was unable to do so..

Any other experiences?

---

### Post by aikiwolfie on 2009-04-27
After watching a few flash videos my sound corrected it's self. Now the DVD drive has decided to stall while ejecting discs. :bang: The most annoying thing about this version of Ubuntu is the sheer randomness of the problems. Something that worked fine yesterday will break tomorrow for no good reason.

---

