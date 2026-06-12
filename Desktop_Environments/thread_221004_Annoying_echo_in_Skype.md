---
title: "Annoying echo in Skype"
date: 2006-07-22
forum: Desktop Environments
---

### Post by joehill on 2006-07-22
Up until recently I was using Skype to talk to friends all over the world, then suddenly (I have no idea what changed in my system) everyone started reporting that they were hearing an echo of their own voice that made it impossible to talk.  Their voice seems to be cycled back into Skype input.  I'm using Skype 1.3 beta with ALSA output, but surprisingly, I get the same problem if I try 1.2 with no ALSA output.  (A similar problem was discussed here [http://ubuntuforums.org/showthread.php?t=42728](http://ubuntuforums.org/showthread.php?t=42728) and as far as I could tell no one resolved the problem.)

I've tried a number of things to try to isolate the problem.  I'm using an external microphone and head set, so the echo is not microphone feedback.  I've set the ALSA mixer to capture but mute the microphone, but the microphone settings seem to have little effect.  Muting microphope capture doesn't solve the problem.  I've tried muting the capture (both for capture and playback) and saving the settings, but when I try to call someone capture is automatically turned back on and the volume setting doesn't seem to do anything.

The only thing that seems to make a difference is changing the PCM setting, which reduces the echo a little but also means I can't hear the person very well.

Thanks!  If I can get this working it will save me a lot of money on phone cards.

---

### Post by roostishaw on 2006-07-22
Hmm... I don't know if this will answer your question, but I was having the exact problem. The other person was using a G5, so the mic was right next to the speaker. They just started using headphones...

---

### Post by joehill on 2006-07-28
Thanks for the suggestion Roostishaw. I have made sure everyone I've been talking to is using a headset that doesn't contribute to feedback, so that didn't turn out to be the problem in this case.

For the benefit of other Skypers out there, I seem to have solved the problem.  Using the gnome-alsamixer, I did File -> Change Device and went to OSS mixer.  I turned the PCM and microphone volume all the way down.  I thought that by using ALSA as Skype's audio interface I wouldn't have to mess with OSS, but I guess I was wrong--I have to adjust both OSS and ALSA.  Won't it be nice when Linux only has one audio system to worry about?

---

