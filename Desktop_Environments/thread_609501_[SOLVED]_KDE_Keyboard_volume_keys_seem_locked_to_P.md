---
title: "[SOLVED] KDE Keyboard volume keys seem locked to PCM"
date: 2007-11-11
forum: Desktop Environments
---

### Post by keyboardashtray on 2007-11-11
Recently switched to KDE.

What I want is for the Kmix volume control in the tray, the keyboard volume & mute keys to all control the same volume channel. 

I can't get the keyboard volume control  keys (increase and decrease) to control what I have selected as the Master Channel in Kmix. 

Whichever I select for master, the Mute key *does *control, but the PCM mixer section doesn't have the green light for muting above it in the list, and when mute "mutes" that, it doesn't affect sound. (So at the moment I'm opting for "Front" to be the master channel, as keyboard mute *will* affect that).

But when I select Front to be the master control, the keyboard volume keys still only affect PCM. I have tried right clicking the Front section, and binding the volume keys specifically to them, but the keys still control PCM. 

This is frustrating because I control volume from all over the place - both from the tray and the keyboard, and it either creates a volume inflation or deflation, where I keep maxing one out because the other is low.

The posts I've read all seem to be about how to find these controls in the first place, or the computer flat out not recognizing the keys.

Can I get these keys to control Front instead of PCM?

Alternatively, can I somehow enable a mute on the PCM? Then I could select PCM as the Master and everyone would be on the same page.

Possible pertinent info: The sound is set to autodetect (would changing it to ALSA or OSS or something be better?)
HDA Intel sound

---

### Post by keyboardashtray on 2007-11-12
Well, I don't know if it was simply a restart that solved it, but when I logged on today it worked. Although I look at the sound system settings and it says ALSA now instead of auto-detect, I thought I had turned it back to the defaults after my experiments.

So I'm not sure if specifying the sound solved it in combo with the restart, or if it was simply the restart.

But now I don't have any on screen display for the volume/mute. #-o

---

