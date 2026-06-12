---
title: "PulseAudio and Ubuntu 10.04"
date: 2010-09-18
forum: Desktop Environments
---

### Post by decatur-linux on 2010-09-18
I recently had difficulty using Skype under Ubuntu 10.04. My audio would not work.  I checked my audio devices under Skype and the only choice that I had was PulseAudio.  I found an article at [http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html) that indicated I should remove completely **pulseaudio** and install in it's place **esound**, which I did.  I then was able to select the proper audio device for Skype and Skype worked fine.

Since that time I have had some strange behavior with my sound under Ubuntu 10.04: whereas before I had no *startup sound*, now I get an abbreviated startup sound that I had under Ubuntu 8.04.  When I go to System-->Preferences-->Sound, I get a pop-up windows that says something like **Waiting for sound to respond**.  Then after a few seconds, the window disappears, but I have no control over sound.

Evidently it has something to do with the removal of PulseAudio but, short of reinstalling PulseAudio I don't know what else to do.

Any suggestions?

---

### Post by kostkon on 2010-09-18
The suggestion is obviously: remove esound, reinstall pulseaudio.

Get the latest Skype from the software centre. Install the *PulseAudio Volume Control* utility that it will allow you to select an input and an output device for Skype (you can do it while Skype is running, open the volume control utility and select the Applications tab).

Removing something that comes by default is always not a good choice. The post you are linking is very old anyway.

And, obviously, it's normal for Skype to be showing only the pulseaudio option in its sound preferences.

---

### Post by Eugene.Bakin on 2010-09-29
About that issue. 
I have same kind of problem. My mic doesn't work in any program I've tried. Pulseaudio monitor simply doesn't show any signal. 
But, if I run alsamixer - I can unmute mic. Now I can hear myself speaking, but not a single program shows a thing.
Any suggestions?

---

