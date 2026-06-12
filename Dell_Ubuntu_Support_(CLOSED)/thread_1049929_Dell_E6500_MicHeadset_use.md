---
title: "Dell E6500 Mic/Headset use?"
date: 2009-01-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by windfix on 2009-01-25
I have a new E6500 running 64-bit 8.10 Intrepid.  I am able to use the onboard mic, but the external mic jack does not seem to work.  I have tried two separate microphones with it.  The headset sound works, but only the onboard mic.

When I use sound recorder, the only "Record from input" option is "Capture".

Clues anyone?  This makes audioconferencing or webconferencing difficult.

---

### Post by windfix on 2009-03-14
Anyone?

---

### Post by Denny Johnson on 2009-03-15
Are you using Alsa mixer?
If you have a speaker icon in your panel, what do you see when you double click it?

---

### Post by windfix on 2009-04-28
Yes, using Alsa mixer.  I upgraded to Jaunty, so double click mutes the speakers, but under Volume Control, I have:

Headphone, PCM, and Front under playback
Capture, Capture 1 under recording
Digital Mic 1 under Options

I have messed around with other recording options (Mux 1, DAC0, DAC1, import mux 1 & 2, Digital input source, etc.)

Never any luck with the mic jack.  It works from XP

---

### Post by Denny Johnson on 2009-04-28
Did you try Analog Inputs instead of Digital Mic 1 under Options?
If that works for the headset, you may need to re set to Digital Mic 1 to use the internal mic.

---

### Post by windfix on 2009-05-18
Partial success, but here's a weirdness:

I installed gnome Alsa mixer utility so I can see all the audio settings in one spot (nice app!).  I CAN get the mic jack to record sound by enabling DAC0 - however, it ceases working as soon as the headphone jack is plugged in!

So.. I can either use the headset mic or the headset earphones, but not both at the same time- :confused:

---

### Post by Denny Johnson on 2009-05-18
Here are some screenshots of what works on my 1420n, 8.04.
Hope it helps, tho your Alsa may look different.
I may have things enabled that don't do anything, but this works for me.

---

