---
title: "Flashing screen savers and blank video palyback in Feisty with compiz"
date: 2007-04-23
forum: Desktop Environments
---

### Post by bartoz on 2007-04-23
I hope this is the right section to post to..

I recently upgraded to Ubuntu Feisty and noticed a problem with video playback.
The fact is that if I play a video i see only a black box (audio is played right) and I can catch glimpses of the video playing only while resizing the window.
The other problem (I think the are related) is that Opengl screensavers (for example gears) are shown somewhat flashing on a black background.

Hope I explained in an understandable way.
Thanks in advance for any help!

---

### Post by Guranic on 2007-04-23
Same problem over here. Compaq laptop with ATI Radeon IGP 330M/340M/350M.

---

### Post by bartoz on 2007-04-24
I forgot to say..
I also have an Ati videocard. Radeon Mobility X700 on an Acer Ferrari 4005.

---

### Post by aSoRaa on 2007-04-24
I'm joining this one. Same problem. ATI Mobility Radeon 9100

---

### Post by bartoz on 2007-04-24
The problem is with compiz..
I tried disabling the Gl Desktop and now everything's working well..
I don't know if this is an already known bug or if there is a fix already..

Hope it can be fixed soon..

---

### Post by bartoz on 2007-04-25
Anyone else with the same problem?

---

### Post by bartoz on 2007-04-29
Tried with Beryl, same problem.
No problem with metacity though..
Anyone has any solution?

---

### Post by bartoz on 2007-04-29
Guys, I got a solution..
It worke  well for me!

look [here](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)
With many thanks to bobbob94..

---

### Post by davidgarcin on 2007-04-29
having the same problem with Compiz and ATI Radeon X300 in Feisty.  When I try the above solution, there isn't an 'output' line.....

---

### Post by davidgarcin on 2007-04-29
hehe.  turns out I'm just dumb.  Specifically, change the "Plugin" selection under Default Output.  That worked fine for me.

---

### Post by Turin Turambar on 2007-05-06
I too had this problem. I fixed it by changing the video output, as you said.

---

### Post by litmus on 2007-05-08
Hi, this is a bit of a flawed solution because when choosing X11 instead of XV for video playback you lose all the hardware acceleration, scaling etc. That is, you lose a lot of quality when playing a video and its extremely CPU consuming (just try to play on x11 fullscreen and you'll know what i mean).

Has anyone found a way of fixing this black video problem WITHOUT having to downgrade the video to X11 (ie. keeping the XV driver????)

Thanks in advance!

---

### Post by nn2s2u on 2007-05-10
iam a newbie to the linux community, and this is my 1st post, but i seemed to have fixed  this without changing my video output (in VLC) to x11. all i did was disable desktop effects. (make sure you actually disable them by clicking on the button "enable desktop effects", don't just uncheck the boxes).

---

### Post by davidgarcin on 2007-05-10
> **nn2s2u said:**
> iam a newbie to the linux community, and this is my 1st post, but i seemed to have fixed  this without changing my video output (in VLC) to x11. all i did was disable desktop effects. (make sure you actually disable them by clicking on the button "enable desktop effects", don't just uncheck the boxes).

well, yeah, we know that's the source of the problem.  "Compiz", what we've been talking about, is the program behind the desktop effects, and we want to keep them on, because they're pretty sweet.

@litmus - I've switched to Mplayer from Totem, and the surprising thing is that it says its using xv and NOT x11.  This is a little strange, seeing as how xv didn't work in Totem or VLC.  And I don't think my experience is very consistent with others', but you may want to give it a try if you haven't already.

---

### Post by litmus on 2007-05-11
davidgarcin- yes, i have noticed that as well. It seems that both the mplayer AND the xine (totem-xine, gxine, etc.) engine does not cause the black screen problem with XV. But i noticed another strange behaviour when using mplayer or xine. If you try to move the window when a video is playing, the video does not follow the window unless you stop moving. This is strange behaviour indeed for the video not to follow the frame.. :-s If anyone finds a solution to any of those problems let us know!!

---

### Post by reckik on 2007-07-29
> **bartoz said:**
> Guys, I got a solution..
It worke  well for me!

look [here](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)
With many thanks to bobbob94..


Yup had the same problem with my ATI mobility 9000 on Dell 600m insprion.. Ur solution worked great! many thx....

---

