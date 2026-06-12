---
title: "World of Warcraft Update Bugs?"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by sedition on 2007-04-03
So, I pulled down the pushed update (2.0.12) today from Blizzard, and now after running for a bit, my system speaker starts beeping. Slow at first, it eventually builds into utter random speeds and pitches. Anyone else having this problem? I haven't made any changes in my config or pulled down any updates from Synaptic (which had caused glitches/stuttering in the past until I reinstall the updates).

Thanks in advance,
-Sed

---

### Post by Gorthus on 2007-04-03
No, I have not had this problem... Do you have your winecfg audio set to OSS or ALSA?

---

### Post by sedition on 2007-04-03
Sound is good, it was the actual system speaker beeping. Mysteriously enough, I just happened to change winecfg to NT 4.0 and everything works fine now. Thanks for the assist, though.

---

### Post by NerdyShinobi on 2007-05-22
> **sedition said:**
> Sound is good, it was the actual system speaker beeping. Mysteriously enough, I just happened to change winecfg to NT 4.0 and everything works fine now. Thanks for the assist, though.

The bit about changing WineCFG to nt4.0 should be in the community docs on this subject.  I happened on this thread because I could never get the updater to trigger, even if I started it manually.  changing the Windows version to NT4.0 got it to pop.  Thanks, Sedition! :KS

---

### Post by laffys on 2007-05-22
Well here's another one for you guys. After the update patch, everything works great -sound's good, graphic's good; but when I quit the game it freezes. Right after I hit the quit button. The system just freezes. Any ideas?

---

### Post by Falcorian on 2007-05-22
> **laffys said:**
> Well here's another one for you guys. After the update patch, everything works great -sound's good, graphic's good; but when I quit the game it freezes. Right after I hit the quit button. The system just freezes. Any ideas?



Same problem, no solution yet.

I also can't seem to exit cleanly. Logout/Exit game buttons press, but do nothing. /logout /camp etc. won't let me hit enter after typing them... Very odd. (EDIT: Seems to be mod related, with them all off I can exit, but I still get the freeze on quit)

---

### Post by laffys on 2007-05-22
Wel I went ahead and turned off my extras and sadly still freezes on the quit or exit. :((

---

### Post by Pikestaff on 2007-05-22
I'm jumping on the bandwagon here, definitely having problems with this update... hangs on exit, I'm seeing the new Terms of Service every time I try to log in (even if I previously accepted them), the launcher is acting up, and the sound, which previously worked for me about 95% of the time, is now only working about half the time.  Furthermore, the game seems to kill my system sound entirely requiring me to restart X...

Hopefully we'll be able to figure out this problem soon though, if no one has yet!

---

### Post by Falcorian on 2007-05-23
I'm getting texture/model errors sometimes... But the new REAL problem is that after about 20 minutes, I get a hard lock up and can't do anything but power off. Can't switch to terminal to kill it, can't restart X, just have to pull the plug.

Using an ATI Mobility 9700 with the newest proprietary ATI drivers, and Wine 0.9.37, I think it might be an ATI thing, but I don't know for sure.

---

### Post by Antrix on 2007-05-25
I am also getting random lockups (can play for 1 minute - 4 hours before it can suddenly lock up). I also have a feeling its ATI related. X850XT.

---

### Post by GvsE on 2007-05-26
Yeah, same problem here! Have anyone solution for that i cant listen music and play wow and same time? Its only one of them but no both? 

Post in wow-europe.com about freeze thing. It blows..
[http://forums.wow-europe.com/thread.html?topicId=286944149&postId=2864904786&sid=1#5](http://forums.wow-europe.com/thread.html?topicId=286944149&postId=2864904786&sid=1#5)

---

### Post by wiztech on 2007-05-27
i was getting the same problem with freeze on exit 

i solved it by setting the world of warcraft folder and al the files/folders inside so that  only the owner get acces and modify  the files and the group and others can't view or modify

don't know if that was the solution for the freeze on exit  bacause i have tried a lot to get this fixed but it is worth trying

hope this helps

---

### Post by GvsE on 2007-05-27
Have anyone tried to chmod them? I guess its normal from bliz that they don't care if we got something to say.. :/

---

### Post by ShadowFlar3 on 2007-05-27
The freeze-on-exit bug seemed to be server-side and if you try it now you won't probably experience it regardless on if you did something about it or not. :)

---

