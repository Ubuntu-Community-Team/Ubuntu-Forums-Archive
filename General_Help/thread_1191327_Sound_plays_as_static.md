---
title: "Sound plays as static"
date: 2009-06-18
forum: General Help
---

### Post by Epidural on 2009-06-18
Recently (the past week or so) all sound playing on Ubuntu has turned to static. When there are no sounds playing, there is no static; but no matter what form of media plays (sounds, music, flash, etc) it comes out as a faint static. I can't think of anything administrative that I've done to cause this except maybe updates? I tried upgrading 8.10 x86 to 9.04 x86 (after the sound stopped working). Still nothing.

This machine is dual-booted to Windows, and the sound on windows (oddly) is working just as it should.

Any help? (=

---

### Post by Epidural on 2009-06-18
Ahh! Did some extra searching, and found that for some reason Alsamixer changed itself to Digital Audio instead of... analog? Or whatever it was before.

I had checked this a while ago, and all was as it used to be. But as I checked again (I must have missed something) the Alsamixer had the "PCM" turned all the way down (whatever that means). 

Hope this helps out anybody else who might be experiencing the same problem!
Turned the PCM up to 100% and all is well in the world of Ubuntu. 

PS: 9.04 seems like it should be an OK upgrade. Everything works as it did with 8.10, at least to the casual user.

---

