---
title: "XFCE+mediabuttons problem"
date: 2012-04-06
forum: Desktop Environments
---

### Post by Amanoo on 2012-04-06
I installed Xubuntu on my laptop, but I have a bit of a problem.
I have an Elitebook 8540p, which has a touch panel with some buttons, among which a few media buttons. My unmute button doesn't unmute properly. I do see a message that implies that it did unmute (or at least, did unmute something), but as you can see on the first screenshot I included "Speakers" under "Built-in Audio Analogue Stereo" stays muted, and so does the speaker icon in the top panel. I believe it is something within XFCE that is causing this, since I have been meddling with other GUIs that didn't seem to have problems like these. I have one other problem, which is that the headphones and the speakers seem to be controlled seperately, which you can see if you compare the two screenshots closely enough. I'd rather have my volume up, volume down and mute buttons control both "Speakers" and "Headphones", so that the states of these two are always the same.

Can anyone help me with these problems? I especially find the mute/unmute button not unmuting properly very annoying.

---

### Post by Lemuriano on 2012-04-06
Same problem here

---

### Post by brainwash on 2012-04-06
The comments on this bug report might help you solving the problem:

[https://bugs.launchpad.net/xfce4-volumed/+bug/883485](https://bugs.launchpad.net/xfce4-volumed/+bug/883485)

---

### Post by Amanoo on 2012-04-06
I am trying to do what number 3, 13 and 14 suggested, but it appears that active card keeps on resetting itself to HDAIntelAlsamixer. I am very curious to what would happen if it didn't do that.

---

### Post by LewisTM on 2012-04-06
Your problem seems to be related to this [thread]("http://ubuntuforums.org/showthread.php?t=1930221"). Maybe the solution can help you.

Cheers!

---

### Post by Amanoo on 2012-04-07
You're officially a hero :D
Disabled that weird Daemon and then set my own keyboard shortcuts. Too bad there is no notification anymore, but I didn't care too much about that anyway. It doesn't seem to like toying around with the mute button, I think it crashes PulseAudio, or something. But not toying around with silly media buttons shouldn't be too hard.
I don't suppose you know why my laptop's browser-button makes the current page in Google Chrome go to chrome://newtab? If we are talking about keyboard shortcuts and Daemons that override them anyway, I figure this is also a problem you might be able to help me solve. Just like with the previous error, it seems that something also has a standard action for XF86HomePage, which again overrides my custom shortcuts. I am not too interested in really digging to deep into it, never really used that button to begin with, but if you happened to know about that too, it would at least make my system a bit less Spartan. The only solutions to it that I found so far are Openbox based. I am fairly sure I am using Xfce/Xfwm and not Xfce/Openbox. This last solution at least did teach me in what sort of direction to look.

---

