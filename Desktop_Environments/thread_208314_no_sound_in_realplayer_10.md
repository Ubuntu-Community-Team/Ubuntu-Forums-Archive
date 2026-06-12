---
title: "no sound in realplayer 10"
date: 2006-07-03
forum: Desktop Environments
---

### Post by The Badmash on 2006-07-03
hi,

i've installed realplayer 10 and have the picture working, but no audio.

audio seems to be working in all other applications, ie xmms, vlc.

soundcard is a terratec ewx24/96,

..but also has intel 82801ba-ich2 on motherboard which is unused. this seems to show up as the default soundcard when i check the sound preferences, no matter how many times i change it to the terratec card.

can i manually swap the priority of these cards, or delete the intel onboard one??

this may not be the problem, but it would eradicate one more element of doubt.


any ideas would be appreciated

---

### Post by Jagot on 2006-07-03
How did you install it?  If you didn't do it already, you could try reinstallign with this method:

[https://help.ubuntu.com/community/RealplayerInstallationMethods#head-16d4b26b1e26b89262d400f91db007f603d3bd42](https://help.ubuntu.com/community/RealplayerInstallationMethods#head-16d4b26b1e26b89262d400f91db007f603d3bd42)

---

### Post by The Badmash on 2006-07-03
initially installed (or rather attempted to) the the .bin file from the realplayer site, but wasn't really working right, so deleted it.

then installed from plf repos without issue, and got picture but without sound.

spookily, it has just now got sound, on about the 5th reboot, and it is slightly jittery.
also terratec card is now showing as default in system > prefs > sounds.

very odd.

---

### Post by The Badmash on 2006-07-03
okay, another reboot and now its back to the intel on-board card as default and no sound on realplayer....

other sound/media apps, such as xmms and vlc are working fine though..  and through the terratec card...?

i am confused.

need to kill the on-board intel sound-chip thingy and hopefully that will resolve the conflict...  i don't know how to do this though.... any advice would be great!

thanks.

---

### Post by The Badmash on 2006-07-03
incidentley jagot.. are you a man of kent or a kentish man?

i was born a kentish man myself, but spent my formative years in east kent.

---

### Post by art on 2006-07-03
I had a similar problem and this solved it:
[http://www.ubuntuforums.org/printthread.php?t=32063&pp=40](http://www.ubuntuforums.org/printthread.php?t=32063&pp=40)

---

### Post by The Badmash on 2006-07-04
thanks, i'll look into it!

---

### Post by RikBlankestijn on 2006-07-15
Have you managed to fix the problem already TB? The suggested link does not cover the problem you have, I got the same problem; [http://www.ubuntuforums.org/showthread.php?t=192316](http://www.ubuntuforums.org/showthread.php?t=192316)

---

