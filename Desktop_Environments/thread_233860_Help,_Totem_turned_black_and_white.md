---
title: "Help, Totem turned black and white"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Serguei_89 on 2006-08-10
Hi, where did all of my color go?

I searched the threads about totem and color problems, but didn't find solution to mine.

I didn't have this problem just 2 days ago. All I've done since then is install kde-desktop and installed all updates. One update was strange in the update manager. It kept saying that there is some update for totem, but it didn't mark it for installation. So eventually I marked the update manually and next time I use totem, no color. Not sure of the title of the update but it said something about both gstreamer and xine. 

Maybe this output has something to do with the problem: (me running totem)

$ totem
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

After that it runs but videos don't have color.

---

### Post by ryP on 2007-06-29
Not sure if this will help you or not, but I noticed a problem with Totem turning black and white also.  It seemed totally random, it would turn black and white all of a sudden, and then come back to color by itself, not even restarting or closing down the app would fix it.

Anyhoo, when it turned black and white one time, I opened Totem up separately (as opposed to running through a browser) and went to Edit -> Preferences -> Display tab.  On the Display tab I noticed that the Saturation slider was all the way to the left.  I hit the "Reset to Defaults" button and it put them all back to the middle.  After that my vids were back in color.  So maybe that will get you back to color....until it happens again.  

I was thinking that maybe it was a movie file or website that was setting that slider all the way to the left.  But since you mentioned you just updated, and I believe I have that update, maybe it has to do with that.  Not sure of the cause, but maybe this will get you by till it gets figured out.

---

### Post by Abik0101 on 2007-11-21
Sorry to update this forum so late at this time. I searched for a similar topic elsewhere in these forums and cud not find it...

Now about the color bug...
I am running Ubuntu 7.10 Gutsy Gibbon. (final release and not any test release). My video hardware is Intel 945GM. (no ATI or nVidia)

I noticed that the first video that I open will not have any colour. If I open a second video (it can be the same file that I opened first) while the first is still running, then the second video does have colour. The third, the fourth and any other new video file I open has colour (as long there is a video file playing when I try opening a new one).

Have to add that this does not irritate me too much. I am posting this just to tell that this bug is still in Gutsy. Sorry if I missed any posting etiquette - am new to all this :-)

---

### Post by bornakke on 2007-12-19
Did you try [http://ubuntuforums.org/showthread.php?t=432197](http://ubuntuforums.org/showthread.php?t=432197)... fixed my problem...

---

### Post by RobbMeex on 2008-01-12
Thanks ryP (It wouldn't let me give you a real thanks)
SO THANK YOU THANK YOU THANK YOU~~:KS

---

### Post by Abik0101 on 2008-01-27
Yes I tried this, but seemed to be working sometimes and not sometimes, so now I switched to VLC. Working fine :-)

---

### Post by BigBananaMan on 2008-07-19
I've tried sliding the saturation back to the center.  Every time I open another video it picks a spot down at the left where there is no color.  Sometimes it works fine but at the moment it just keeps changing to B&W.

Edit: I have noticed just now that when I slide hue all the way to the left, it only moves the saturation bar about 1/10 of the way with each video I open.  The top bar also moved slightly to the left.  Something must make totem want to balance the bars for secret reasons.

---

