---
title: "PulseAudio gives Connection Refused"
date: 2009-05-18
forum: General Help
---

### Post by nazgul42 on 2009-05-18
I am trying to get a bluetooth headset working on Jaunty, but I don't think that that affects this topic too much.  Whenever I try to do something with PulseAudio, such as pactl or padevchooser, it gives me the error Connection Refused or Connection Terminated.  I don't understand what is happening here.  I have kubuntu 9.04 installed on my PC, but I also installed gnome on it if that makes any difference.

---

### Post by nazgul42 on 2009-05-19
OK... I tried running pulseaudio in the terminal, and I tried the command:
pactl load-module module-alsa-sink device=btheadset
that command worked, but when I looked at where pulseaudio was running, it had crashed, saying "E: module-alsa-sink.c: Assertion 'err != -11' failed at modules/module-alsa-sink.c:226, function try_recover(). Aborting."
It seems like trying to use the bluetooth headset with pulseaudio crashes it... Is it possible that there is an update for it that I am missing?  Thanks for any replies.

---

### Post by HavocXphere on 2009-05-19
You do know that PulseAudio goes with ubuntu and not kubuntu? The entire sound setup on kubuntu is different and I'm not surprised that its not working.

Nonetheless, I'd *guess* that you need to remove existing sound servers first since they are probably blocking the soundcard. But this will be kinda tricky since Phonon etc is integrated into Kubuntu pretty hardcore.

---

### Post by nazgul42 on 2009-05-19
Thanks, I am entirely new to sound on Ubuntu...
Would it be easier to just reinstall it as Ubuntu instead of kubuntu, or is there a fix that would work for this?

---

### Post by nazgul42 on 2009-05-19
OK, so I installed Ubuntu 9.04 instead of Kubuntu 9.04, and the same thing still happens.... I guess that wasn't it....

---

