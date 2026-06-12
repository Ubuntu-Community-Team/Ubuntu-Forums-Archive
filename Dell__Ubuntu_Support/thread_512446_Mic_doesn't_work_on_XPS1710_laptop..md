---
title: "Mic doesn't work on XPS1710 laptop."
date: 2007-07-29
forum: Dell  Ubuntu Support
---

### Post by FreeSoul on 2007-07-29
I have a dual boot and the (external) mic works in XP, but not with Fiesty 7.04. 
I've installed the alsa sound packages but that didn't seem to make a difference, though I didn't really know if there was something particular I should have done, was a recommendation.

Under System - Preferences - Sound
"**Sound Capture**" under "**Audio Conferencing**" is on "**stac92xx Analog**". No matter what I choose it it freezes up and says:

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

And EVERY time The sound preferences box freezes up and I have to "force quit" it, to get out.

Any ideas? I really want to use skype from Linux and not Windows...

THX,
FreeSoul

---

### Post by FreeSoul on 2007-07-30
Anyone? :(

Just a point in the right direction please.

Thank you,
Free Soul

---

### Post by Luke.Hoersten on 2007-07-30
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_recording_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_recording_does_not_work)

This could be it?

---

### Post by FreeSoul on 2007-07-31
Oh boy, now i don't have any sound at all.
The speaker symbol next to the time has a cross through it.


I did it this time... :(

Next question, since the realtect install was unsuccessful how can I "uninstall" it?

---

### Post by fergie4000 on 2007-08-04
Make sure you run the install as root. And I have just had the exact same problem on a Toshiba Equium L20-197 which I believe has a Realtek soundcard. Will this fix help me?

---

