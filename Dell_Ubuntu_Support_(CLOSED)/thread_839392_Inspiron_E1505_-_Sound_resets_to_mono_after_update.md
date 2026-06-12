---
title: "Inspiron E1505 - Sound resets to mono after update"
date: 2008-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ibeleaf on 2008-06-24
My sound is only coming out of my left speaker, i know my right one isn't blown.

Sometimes if i mess with the sound settings i can get it to two stereo again... but everytime an update comes out it resets it back to mono it seems... and right now i cant get it to go back to stereo.

Is there something i can type in terminal to give an output of my sound settings to help with a solution?

---

### Post by ibeleaf on 2008-06-25
bump

---

### Post by madler on 2008-12-14
Had the same problem with a Thinkpad T60 (AD1981 audio),
some updates seem to mess with the sound settings.
Open volume control, select the device which has '(OSS Mixer)' after it and see if one of the channels has been set to volume zero.
Adjust as needed ;)
That fixed it for me.

---

