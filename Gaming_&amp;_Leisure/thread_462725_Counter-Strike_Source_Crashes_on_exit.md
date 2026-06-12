---
title: "Counter-Strike Source Crashes on exit"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by Copperteeth on 2007-06-03
Hello everyone

I purchased a Transgaming subscription today and installed Counter Strike Source on Ubuntu. I got it working. It ran real bad though even when bringing all the settings to the bare minimum and installing Caseys CSS script. The game was unplayable IMO at arround 10 - 30 fps. So i decided that i should look arround for solutions to why it wouldnt run well. I came across the answer: Cedega is a massive memory hog. The solution: Wine, i coulda saved myself some money by just using wine. To make a long story short, I got CSS working great at 30 - 70 fps on decent DX8 settings.

Now here comes the bad part. When i want to exit CSS, the game crashes! This locks up everything and even ctrl + alt + backspace will not reset anything. I was wondering if someone could point me in the write direction about this. I know its possible to exit without any problems because Cedega, as crappy as it performs, exits properly.

Im using a GeForce 6200 with newest Nvidia drivers
Beryl and Compiz are not on
Using ubuntu 7.04
wine version 0.9.38
Compatibility is set to windows 98 because i guess it runs best

those are the only things i can think of that may help.
 Thanks in advance

---

### Post by Feba on 2007-06-03
I had a similar problem... are you SURE compiz is off? Do a quick 'metacity --replace' every time before you start, sometimes the simplest answers are correct.

---

### Post by Copperteeth on 2007-06-03
Yes, i dont run desktop eyecandy for the reason that it uses resources with little to no benifits. I think it has something to do with screen resolution changes, im going to try some things right now but if i could get some help still id apprecate it!

---

### Post by Rocket2DMn on 2007-06-03
I run cs 1.6 through wine (I was amazed I got it to work).  Though it lags a bit, it's still worth it.  I've had cs freeze on me at 2 points: 
1) joining the game
2) exiting
I've surfed forums and a lot of people seem to think it may be the sound mixer.  Most people suggested using OSS, but it still froze sometimes for me.  I've been using ALSA the last few days, but it's too early to tell.  In any case, it's worth a look at if you haven't solved the problem yet.
Good hunting!

---

### Post by Feba on 2007-06-03
Have you tried doing "killall esd" before you start? That solves every problem I've had with sound.

---

### Post by Rocket2DMn on 2007-06-03
> **Feba said:**
> Have you tried doing "killall esd" before you start? That solves every problem I've had with sound.

I think I'll give that a try, but my learning curve is still a steep one.  What exactly does that mean/do? (I know what killall is)

---

### Post by Feba on 2007-06-03
According to man, ESD is a sound daemon. I assume shutting it off keeps it from getting in the way or allows it to release resources or something. I don't really know, I was told to do it, and it worked. I've tried it ever since then when I had sound problms with something, like et, and it works pretty consistantly.

---

### Post by Rocket2DMn on 2007-06-04
Very well then.  I have heard that programs competing for sound can be the source of some of the problems.  Perhaps one of the mixers is just better at handling that problem.
I'll give that "killall esd" a try.  Thanks.

---

