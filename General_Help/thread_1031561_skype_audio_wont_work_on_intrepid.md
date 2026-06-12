---
title: "skype audio wont work on intrepid"
date: 2009-01-05
forum: General Help
---

### Post by thingy87654321 on 2009-01-05
i have skype and ubuntu 8.10, with intel ich6 (that is what it says in the volume control panel, skype wont work, i have tried every audio device listed in the sound devices on the skype menu, it works fine with ubuntu 8.04 tho

---

### Post by Guille Damke on 2009-01-05
Can you post which options you have for "sound in" in Skype? In my case I set it to "HDA Intel(hw:Intel,0)".
I also run 8.10 and I have set in my machine "sound out" and "ringing" to "pulse". This should work at least if you press the "make a test sound" button.
For talking, you also have to go to the "speaker icon" next to the clock , right click to open volume control, go to preferences and activate the "capture" switch. Then, move this volume in the "recording" tag up, to control the volume of your mic. Probably, you'll also have an "input source" control (activate it), to choose among your mics (usually a front-mic for the built-in one, and a "mic" for a microphone plugged to your sound card input).
Good luck.

---

### Post by thingy87654321 on 2009-01-05
default
intel ich6 (hw:ich6 4)
hdmi
pulse
headset
hw: ich6 :0
and other ich6 ones

---

### Post by thingy87654321 on 2009-01-05
default
intel ich6 (hw:ich6 4)
hdmi
pulse
headset
hw: ich6 :0
and other ich6 ones

---

### Post by thingy87654321 on 2009-01-05
i changed ringing and auido out to "pulse" and the audio in to" intel ich6 (hw: ich6,0)" and it works now, thanks:D

---

### Post by Guille Damke on 2009-01-07
You are welcome!
It's good to know that it worked.
Don't forget to label the thread as solved.
Guille.

---

