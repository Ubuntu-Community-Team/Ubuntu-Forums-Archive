---
title: "Verry Pissed. Sound not working no matter what i try"
date: 2009-01-18
forum: General Help
---

### Post by d3drocks on 2009-01-18
So, i had do reinstall ubuntu, because windows destroyed grub. i know thats not usually a reason to reinstall, but i was having JACK issues before and this was a possible solution.
BAD MOVE ON MY PART!
after the reinstall, i start up ubuntu, and BANG. no sound!
I played with ALSA and OSS, changed a few settings, Tried EVERY F****** AUDIO OUT PORT ON MY PC, STILL NOTHING!
(and before it gets said, no the system is not on mute). i have no idea whats wrong, and its DRIVING ME NUTS!
worked fine a week ago before reinstalling.
EDIT: its not that it cant find the audio devices, because i remember in the past, rhythm box would give me an error when i tried to open music.

---

### Post by Gondee on 2009-01-18
Whats your audio hardware?

Do you have a sound card?

Does the sound icon appear on the top right of the bar?

---

### Post by d3drocks on 2009-01-18
> **Gondee said:**
> Whats your audio hardware?

Do you have a sound card?

Does the sound icon appear on the top right of the bar?

yes, and ive got onboard realtek hardware. ALSA and OSS defenitly detect it. they accurately list every output and input on my pc.

---

### Post by Taidgh on 2009-01-18
I'm getting the same thing. Someone told me it could be an issue with PulseAudio, but trying to fix that just made it worse.

---

### Post by d3drocks on 2009-01-18
i dont know why but it started working. I rebooted, and Ubuntu crashed starting up. i hard rebooted, and it just worked. i dont know if this will happen again next time i start up though

---

### Post by d3drocks on 2009-01-28
Its doing it again....
It makes the log in sounds, but after that, no sound at all.

---

### Post by d3drocks on 2009-01-28
> **d3drocks said:**
> Its doing it again....
It makes the log in sounds, but after that, no sound at all.

bump...

---

### Post by Ziggy72 on 2009-01-28
Have a look at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578).

Worked for me.... Good luck

---

### Post by d3drocks on 2009-01-29
> **Ziggy72 said:**
> Have a look at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578).

Worked for me.... Good luck

thanks. that seemed to work.

---

