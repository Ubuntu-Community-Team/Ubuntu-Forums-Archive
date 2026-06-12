---
title: "Poor sound, found how to fix, just can't apply it"
date: 2005-05-02
forum: Desktop Environments
---

### Post by railz68 on 2005-05-02
Installed ubuntu Saturday. Having trouble with sound and nvidia drivers.

The sound was just plain awefull, in everything. Well playing around some more in "alsa-mixer", I found what looked to be some strange values. Some of the "EMU10K" that have a "left-right" value, were different. Example, Left would be at 0, right 60. Just looked like a plain mess.

Using arrow keys, brought it down to zero, then when I brought back up, they now had equal "left/right" values.

In between "AC97" and "SB LIVE", there are 11 EMU10K settings. I have them where sound is good. But opening a different mp3 to test, all the values go back there messed up state. I can see this happen just at the moment I click "play". I wrote the values down, I put them back, sound is good again.
If someone can tell me how to "save" these values, I believe my sound will be corrected. I see no way to save settings.

Of those settings, number 11 (beside the SB Live), makes the biggest diiference.

thanks for any help.

edit/update:  seems to have stuck. Don't know why it wouldn't for 1st couple of trys. Tried a few different tunes, seems good. Hope this helps someone else out.

edit: logout, login, settings are gone. Must be some way to save settings.

---

### Post by nad on 2005-05-02
sudo alsactl store

And while your at it:

sudo chgrp audio /var/lib/alsa/asound.state
sudo chmod g+w /var/lib/alsa/asound.state

So that you can save settings as a regular user of group audio.

---

### Post by railz68 on 2005-05-03
thank you, that did it.  It didn't apply to the other accounts, but I should be able to fiqure them out now too.

My lucky day, fixed sound, and video    :-P 

Re-installed nvidia drivers, no lock ups so far.

---

