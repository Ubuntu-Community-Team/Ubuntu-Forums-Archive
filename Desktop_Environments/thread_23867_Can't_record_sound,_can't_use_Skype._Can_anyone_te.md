---
title: "Can't record sound, can't use Skype. Can anyone tell me how to do it?"
date: 2005-04-04
forum: Desktop Environments
---

### Post by KongeOdin on 2005-04-04
I have read around on the forums but can't seem to find a solution or method to get the mic to record i Kubuntu.
It seems like the mixer being used is the Kmixer 2.4. 
I'm using the KDE3.4 package in Kubuntu. I have enabled the sound system in sound and multimedia and hooked the full duplex box.
Everytime someone calls me on skype I can hear them perfectly but they can't hear me.
I can hear the sound from the mic in my headphones, but can't record it.
Whenever I play an mp3 and press record when using audacity, the sound from the mp3's will be recorded. The problem is that I can't record the sound from my mic.

Do any of you know how I can set my system to record the sound from my mic and send it to a file or to the net with skype?

---

### Post by saltydog on 2005-04-05
I am using Gnome, but I have *EXACTLY* the same problem... Alsamixer is set form microphone capture, but it doesn't capture anything.

---

### Post by KongeOdin on 2005-04-06
Yes it is quite frustrating, but now I know that at least one other person has the same problem. Now I have started to use the line two input instead for my mic (From the external panel of my Audigy PlatinumEx), but I still have the same problem. It is probably not hardware related as I can hear myself speaking in the mic. Only problem is of course that the one I am calling cant hear me.

Is seems I can capture and record sound from mp3's by simply playing them with kaffeine player while recording in audacity.
So to refrase the question. 
How do I capture and record sound from mic or line2 in the Kmix - KDE's full featured mini mixer?
How do I choose to record sound at all from this channels?
Should I be using another driver than the ALSA OSS?

---

### Post by KongeOdin on 2005-04-06
I found a way. The sound is crackling, but at least its working.

1. Started AlsaMixer (v1.0.8 ). Wrote : alsamixer in the command terminal window to start it up.
2. Once started I adjusted things for the n'th time, when I came up with the idea to see what the tab button did for me.
3. Pressed tab and saw that it changed the "View" between Playback(default),   Capture and All.
4. Switched to Capture.
5. increased the neccessary volumes (mic or linein depending of where I chose to connect my mic).
6. Understood that the input applet actually where missing in Kmix - KDE's full featured mixer. aaarrrgghh.
7. Started Audacity from the command terminal and tried to record, which worked with lots of crackling ggghhh.

At least now it works. Hope somebody can use the method.

The next natural question to you would then be: 
How do I make the input tab contain anything in Kmix?

---

### Post by pampa on 2005-04-18
[QUOTE=saltydog]I am using Gnome, but I have *EXACTLY* the same problem... Alsamixer is set form microphone capture, but it doesn't capture anything.[/QUOTE]

I don't know if you solved this problem yet but after many hours looking for an answer I found something.

My system did not record anything even if in alsamixer, in the capture view, the mic was at 100%.  In one webpage I found, it was mentioned that you need to put it in "capture" mode.  This is done with the space key over the "Capture" control.  After doing this, the control has a red "CAPTUR" under it which didn't have at the beginning and an L and R on each side.

Try it to see if that was also your problem.  Hope it helps.

Santiago

---

### Post by bobby555 on 2005-05-19
Tried the alsamixer at command prompt thing, and now it seems my microphone is working!

Haven't had a chance to try it out with skype yet, but i will tomorrow..

AM

---

