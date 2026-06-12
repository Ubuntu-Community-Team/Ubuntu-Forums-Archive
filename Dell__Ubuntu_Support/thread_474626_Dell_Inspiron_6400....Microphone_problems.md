---
title: "Dell Inspiron 6400....Microphone problems"
date: 2007-06-15
forum: Dell  Ubuntu Support
---

### Post by smitty2point0 on 2007-06-15
Hello all! I'm having some trouble with my microphone not recording properly. When I open sound recorder and speak into the mic, I get no playback UNLESS I save the file. I then play the file, and the recording is there, but very low sound. My sound in general is working great. I have gtk-recordMyDesktop installed, and when I record, the voice quailty is very low and choppy at best. 

I have gone to system>preferences>sound and the ASLA is chosen under "capture". When I test, it locks up after 2 bars and just hangs out there FOREVER. it does the same if I choose any other option.

I have a Dell Inspiron 6400, 2 gb RAM, ATI radeon X1300 128mb. It has the standard Media Direct 3.0 sound option with the 2.5mm jacks or whatever size they are on the side. I'm attemping to use a logitech headphone - mic combo set with 2 seperate jacks, 1 for the mic jack, and one for the sound. Sound output works fine with the headset.

I'm running Ubuntu Fiesty Fawn with beryl.

Any help would rock the house!

---

### Post by neptho on 2007-06-15
The ALSA Intel HD driver seems to only support simplex, which means you can either record, or listen; not both at the same time.  I've made a few attempts to make it work, but I haven't bothered TOO hard, as if I could make it work, I'd be pestered endlessly over Skype.

Good luck.

---

