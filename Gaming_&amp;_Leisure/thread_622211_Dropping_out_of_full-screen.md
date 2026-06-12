---
title: "Dropping out of full-screen"
date: 2007-11-24
forum: Gaming &amp; Leisure
---

### Post by road_rage on 2007-11-24
I am a n00b and trying to adapt to full Ubuntu life. 

One thing I am working into is gaming and have had limited success and now lookign for assistance/direction as I have been searching answers for last three days and have yet to find resolution. 

First issue I noticed is after installing ETQW. Install went well and and after launching game I adjusted resolution settings accordingly and launched game. I am able to play the game for a few moments and then I am kicked from full-screen and loose ability to control either my in game window, or my desktop. I then open a new session, log-in, kill the game process, and return to my session and all is well again ? I have tried to restart the system and check running processes prior thinking it was either an IM or other program stealing priority, but have had no luck resolving. 

I then assumed it was the game I was playing and then installed WOP, again install went well, launched the game, can play for a few moments and then game is windowed and loose all ability to control either desktop or windowed game ? 

As stated, I have searched high and low and have read MANY posts to try to see if this has been reported by others, but I have not found and resolution and would appreciate any suggestions. 

TYIA,

--RR

---

### Post by finito on 2007-11-24
Applications-> wine-> Configure Wine - > Graphics -> Emulate Desktop check it 

This will make the game start in a Windows that you choose the size of..

Basically not full screen..

---

### Post by road_rage on 2007-11-24
Thank You for the response, but not really applicable to my Q:. The games that I am referring to are native Linux ports, not windows games and not in any way using wine. 

Anyone else offer some advice ?

--RR

---

### Post by badrunner on 2007-11-24
Don't use compiz (i.e desktop effects). Its a very poor window manager (its a great compositor), and has all sorts of problems, it really shouldnt have been made default in gutsy. If you turn off desktop effects you wont have any problems with full screen games, native like etqw or those running in wine. Perhaps in time compiz will come close to being a good real world window manager, but at the moment its not really more than a glorified tech demo.

---

### Post by road_rage on 2007-11-25
Thanks for the reply, but not sure if compiz iz the root cause or not as it appears to be more related to the screen saver. 

I have made progress and/or a work around for now. If I disable the screensaver from auto-run from innactivity then I am able to play all games w/ out issue. Issue is some home related to the screensaver taking priority and then forcing the game out of full-screen. I will continue to pursue causes as I hope this will help someone in the future. 

And not to disregard your oppinion of compiz, but mileage may just vary as I have been running for a little more then a month and have yet to see any issues. I have added to it AWN and have lots of effects running and have been loving the eyecandy it provides. Sorry to hear it is not the same for you. 

More to come...

--RR

---

### Post by p-stone on 2007-12-07
I have the same issue as road rage, resolved in the same way, by setting my screensaver to not come on for 2 hours. Two issues with this, one, I like my screensaver, and more importantly I'm using a plasma display and actually kind of need the screensaver to prevent image retention. I'm not at home now but I will try disabling compiz and see if I can use my screensaver, although I suspect not.

---

### Post by p-stone on 2007-12-08
Turning off compiz worked. Now I can play fullscreen games even with my screensaver set to activate after a minute. It's too bad that my windows don't wobble anymore, I guess I'll have to wait for compiz to get updated

---

### Post by kevinfishburne on 2008-02-11
See bug 163865 in Launchpad ([here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/163865")).

The bug's been confirmed but not assigned or given a priority. I'd say it's a fairly serious issue and hope it will be addressed reasonably soon. I sell desktop PCs and having to tell my customers that they need to disable the screensaver is pretty embarrassing to say the least.

Kevin

---

### Post by TaTaE on 2008-05-04
There are two solutions for this. Try one of these:

1. Start Advanced Compiz Settings and disable "Unredirect Fullscreen Windows" in "General Options --> General".
2. Second solution is here [http://ph.ubuntuforums.com/showpost....2&postcount=10](http://ph.ubuntuforums.com/showpost....2&postcount=10)


Cheers,

---

