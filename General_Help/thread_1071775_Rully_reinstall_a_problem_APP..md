---
title: "Rully reinstall a problem APP."
date: 2009-02-16
forum: General Help
---

### Post by its_jon on 2009-02-16
*Title typo !! Rully should read Fully*

My problem is with the App Musescore

A Musical notation application.

It uses midi and has its own soundfonts.

I installed it and it worked great !.....
I altered some config settings to do with midi/soundfonts from within the app and I cant seem to get it working again.

Not being very Linux savvy yet I thought the quick solution would be to reinstall it.

I did a 'complete' removal of it through synaptic (not just the removal)... I rebooted ... then reinstalled Musescore through Add Remove .....

Exactly the same problem !

The problem being that I have no sound and no playback of the scored music.

I am assuming that the app possibly has some corrupt config file somewhere that it is reading on reinstall.... A config file that has not been removed by synaptic...

The Linux file system is still a bit of a puzzle for me......

Help.

I have asked for help on the Musescore forum as well....however it may well be that the problem is my lack of knowledge with Ubuntu.

Help.
:D

---

### Post by sumguy231 on 2009-02-16
It's actually probably a conflict between PulseAudio and ALSA rather than a config file, because I'm having the same problem and I've never installed it before. I'll get back to you if I figure it out.

---

### Post by sumguy231 on 2009-02-16
Oh, and this is the error output I get:
Suspending PulseAudio
Alsa_driver: the interface doesn't support mmap-based access.
init ALSA audio driver failed
no ALSA audio found
sequencer init failed
Couldn't resolve property: 2
Couldn't resolve property: 2
Couldn't resolve property: 2

This is unusual because I'm fairly sure every other app using ALSA works fine on my system through the alsa-pulseaudio compatibility package.

Edit: And for the record it attempts to suspend PulseAudio whether it is running or not. I would say this is probably dumb/broken behavior on the application's part.

---

### Post by its_jon on 2009-02-16
Thanks......

I had to follow some instructions to get rid of pulse and install alsa to get sound at all on my system....

Musescore was working fine on my machine until I tampered with the apps I/O tab in the App's preff's

As I have uninstalled it and then reinstalled it I am assuming a config file stiff hung around... being from a XP background that has happened to me before.... you think you have uninstalled something but the config files stick about.

Where is this app saving such files so I can seek and distroy ?.... assuming this could be the issue.

---

### Post by sumguy231 on 2009-02-17
The Muse configuration is in ~/.config/MusE, deleting that folder should wipe out the configuration. But I can't guarantee that it will actually help with the audio problem.

---

