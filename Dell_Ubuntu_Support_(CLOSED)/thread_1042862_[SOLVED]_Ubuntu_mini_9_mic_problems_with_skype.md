---
title: "[SOLVED]: Ubuntu mini 9 mic problems with skype"
date: 2009-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rolexel on 2009-01-18
I had issues with getting the Mic working on Skype with Dell Mini 9. 
I tried with Ubuntu 8.10 Intrepid Ibex.

This is how i fixed it:

Skype setup:
In skype select Options, then Sound Devices.
Sound In: Set to HDA Intel (hw:Intel,0)
Sound Out: Pulse
Ringing: Pulse

Ubuntu setup:
Select Volume Control, Make sure device: is HDA Intel (Alsa mixer)
Select all check marks in Preferences.
In 'Playback', set Mic Boost to about 80% (I didn't touch Internal Mic Boost)
In 'Recording', Your mic's volume is 'Capture 1'.
In 'Options', select both captures to Front Mic. (If you don't see two Input Sources here, then close Volume control and reopen).

This should help with everything working. Hope this helps.

---

### Post by sirebral on 2009-01-18
Do you think if you installed the drivers that came with your Mini 9 that would help?

I am curious because I still have the pre installed OS and all my Skype settings are set to default.

---

### Post by nwilliam3 on 2009-01-19
This seems to be an issue with 8.10 vs. 8.04 and Dell. I have a 1525n and I had no issues with 8.04, but I haven't been able to get the mic working right in 8.10 yet. I don't use it much so it hasn't been a big issue. I'll try the solution above and see if it works for me. Thanks

---

### Post by rolexel on 2009-01-21
I installed the official ubuntu 8.10 on my mini 9. Its not the Dell version.

That said, my mini came with windows XP, which I gladly erased.

---

### Post by SyberKowboy on 2009-01-21
have you found a way to clean up the audio quality? Test calls sounds terrible.

---

### Post by erlguta on 2009-05-16
Thank you. This solved my problem with skype form medibuntu in my Dell mini 9 wit ubuntu jaunty netbook remix.

---

### Post by ugm6hr on 2009-06-11
This appears to work on Jaunty, but there remains a lot of background noise from the mic.

---

### Post by ugm6hr on 2009-06-14
A better solution for 9.04:
[http://www.ubuntumini.com/2009/04/skype-on-dell-mini-9.html](http://www.ubuntumini.com/2009/04/skype-on-dell-mini-9.html)

Similar, but the settings work without background noise.

---

