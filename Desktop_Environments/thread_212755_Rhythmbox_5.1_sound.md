---
title: "Rhythmbox 5.1 sound"
date: 2006-07-10
forum: Desktop Environments
---

### Post by finalbeta on 2006-07-10
How do I make totem/rhythmbox use 5.1 sound? (it works inside xine because in xine I can set that inside the options)

My Card can output up to 7.1. issen't there a central place I can set the way to output sound to 5.1?

---

### Post by finalbeta on 2006-07-11
Still looking on how to get 5.1 out of Rhythmbox.

Please help.

---

### Post by bojzi on 2006-07-11
I don't think that you enable it directly in Rhythmbox (at least I did it differently). What I did was:

Double-click on the speaker in the upper right corner and go to Edit -> Preferences. Now, here you have to enable everything that you want to control. The problem, at least in my case, is that all speakers, except for the 2 front ones, were turned all the way down.
After enabling everything you want click Close and in a few minutes, through trial&error it should be working (I hope :)).

---

### Post by punkrockguy318 on 2008-02-06
> **bojzi said:**
> I don't think that you enable it directly in Rhythmbox (at least I did it differently). What I did was:

Double-click on the speaker in the upper right corner and go to Edit -> Preferences. Now, here you have to enable everything that you want to control. The problem, at least in my case, is that all speakers, except for the 2 front ones, were turned all the way down.
After enabling everything you want click Close and in a few minutes, through trial&error it should be working (I hope :)).

Unfortunately, this probably isn't the case.

Even if you're levels are set correctly in the mixer, if the sound file you are trying to play isn't in 5.1, it will only come out through your front two speakers.

This being said, there is a way to configure ALSA (the sound system) to duplicate the front two speakers to the other speakers.  However, I have not found a way to do this that has worked properly.  If someone else could shed the light on setting this up, that would be greatly appreciated.

---

