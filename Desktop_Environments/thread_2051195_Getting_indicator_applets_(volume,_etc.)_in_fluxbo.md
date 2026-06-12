---
title: "Getting indicator applets (volume, etc.) in fluxbox"
date: 2012-09-01
forum: Desktop Environments
---

### Post by chogg on 2012-09-01
What program runs the indicator applets in Unity?  I ask because I want to get them in fluxbox.

I already have the network app, nm-applet, running.  It shows up in the bottom right of the toolbar and works just fine.  But I don't know what the other applets are called.

Thanks!

---

### Post by chogg on 2012-09-02
Sorry to bump, but surely it's an easy question for someone who knows the answer, right?

I wanted the network applet in fluxbox.  I knew the name of the program ("nm-applet").  I ran that command in fluxbox, and it showed up just fine.

Now I want the volume control applet in fluxbox.  How can I go about finding out the name of the command which runs it?  Any ideas?

---

### Post by d.atanasov on 2012-09-02
Hi, 

I think that systray applet was indicating all the information in the right up corner. Maybe now it is change but you can make some google to find out. 


cheers

---

### Post by chogg on 2012-09-08
Your response helped me with some ideas about what to google.  Eventually, I found that `gnome-sound-applet` appears to be the closest.  However, there are still several important features missing:

[LIST]
[*] There is no popup showing the current volume level.  (The indicator-applet shows the level only coarsely: there are three wavefronts coming from a speaker which are either colored or not.  It takes about 10 keypresses to change the displayed level!)
[*] In fact, it doesn't appear to handle volume-button keypresses at all!  The only reason volume up/down works is because I manually added entries in `~/.fluxbox/keys` mapping them to `amixer` commands.  Due to (what I presume to be) a bug in `amixer`, the mute button only mutes and does not unmute.  (Yes, I am using the `toggle` command.)
[/LIST]

I *know* the "popup" functions still work, because they do for other applets (e.g. `nm-applet` tells me when my wireless connection is established).  So perhaps the question is: why doesn't `gnome-sound-applet` in fluxbox grab my volume keypresses?  Or if someone thinks the problem lies elsewhere: what else should I try?

---

