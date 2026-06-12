---
title: "No Sound. At all."
date: 2005-11-17
forum: Desktop Environments
---

### Post by Ethan_bennett on 2005-11-17
I have no sound. It reads my on-board C-Media controller, but when I click "test" in Multimedia System Selector, ALSA, OSS, and ESD all turn up with a "unable to open test pipeline" message. I've done the procedure in the Unofficial beginners guide, I've tried activating analog over digital (or is it vica versa?) using alsamixer, no dice. I've scanned the forums, only to find many people with my dilemma, and no response. Does ANYONE know what I should do?

---

### Post by tonysathre on 2005-11-17
do u have the drivers installed and configured correctly? are u running hoary or breezy? 
also check out these threads i found:
[http://ubuntuforums.org/showthread.php?t=21211&highlight=on-board+C-Media+controller](http://ubuntuforums.org/showthread.php?t=21211&highlight=on-board+C-Media+controller)
[http://www.ubuntuforums.org/showthread.php?t=90262](http://www.ubuntuforums.org/showthread.php?t=90262)

it might be that your kernel isnt loading the modules for your sound card, maybe try searching the forums for threads that have problems with the same card
try running an "lsmod | grep snd" to see what module your card uses, if any

---

### Post by Ethan_bennett on 2005-11-17
Ok, here's what I've discovered. My soundcard is present. I can see it by going the device manager, and under "unknown-> CM8738" And a bunch of sound devices. In my Multimedia System Selector,I always recieve "could not create test pipeline" or something to that effect. I've tried just about every Hoary(I'm in Breezy) fix (Recompiling drivers, alsamixer, even adding snd- stuff to my modules list) . I've tried fiddling with my volume manager and my "sound" option in the administration heading. Here is my problem: Everything works, but I cannot unmute my main sound channel(PCM) in the "Capture" heading. If I drop the volume all the way to the bottom, i can unmute it, but when I raise the volume, it becomes muted again. That's all I can figure out. My only other idea would be to check if nvidia has any special drivers for the audio controller. I don't know. any help would be appreciated.

Edit: I have an nForce3 chipset, Cmedia 8738 sound device, 6600gt card. I wanna get CedegaCVS going so I can game, but I need my sound before i even think about that.

---

