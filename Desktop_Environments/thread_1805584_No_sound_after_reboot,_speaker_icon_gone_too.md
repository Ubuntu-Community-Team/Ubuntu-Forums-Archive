---
title: "No sound after reboot, speaker icon gone too"
date: 2011-07-16
forum: Desktop Environments
---

### Post by Mappenz on 2011-07-16
Hi,

ever since i installed xubuntu i have this issue, where i can't turn the sound with the keys back on if i shut down my laptop with sound muted. Since i could turn it back on with the speaker icon i didn't care too much. But now this icon is missing too. The Envelope is also missing. I still have batterie and wireless.

I tried to follow some instruktions to fix sound problems. Thus i know my card is recognized and ```

michael@michi:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono

``````

 amixer set Master toggle

```doesn't fix the problem. fn + f8 neither, even though i geht a notice about turning the sound on/off.

I couldn't find this thread with search>find all your threads. Now i figure i maybe couldn't find a similar thread i opened a few hours ago. Until now i thought it just got lost. If this is a double post it just delete it.

---

### Post by Toz on 2011-07-16
About the speaker indicator icon, make sure that the **indicator plugin** is added to the panel. Right-click the panel where it should be, select "Panel->Panel Preferences" and then go to the "Items" tab. If Indicator Plugin is not listed, click the + (plus) and add it.

---

### Post by Mappenz on 2011-07-19
ok, i found a speaker icon, it works, but it is not what i had.

---

### Post by Toz on 2011-07-19
Did you add the item called "indicator plugin"?

---

