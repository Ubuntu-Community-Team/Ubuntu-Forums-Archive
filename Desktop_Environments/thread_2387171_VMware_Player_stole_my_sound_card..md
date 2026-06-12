---
title: "VMware Player stole my sound card."
date: 2018-03-15
forum: Desktop Environments
---

### Post by TechnoJunky on 2018-03-15
I have Kubuntu 17.10.  I installed VMPlayer 14 today and now I have no sound in KDE.  The VM does, but not my host.  The host has no sound even before starting VMPlayer.  When I go to audio settings, it says I have no input or output devices available.  Rather than screwing with it I decided to uninstall VMware Player and deal with it later.  Unfortunately I still have no sound, even after rebooting.  

When I run plusaudio at the command prompt, I get this.

E: [pulseaudio] module.c: Module "module-switch-on-connect" should be loaded once at most. Refusing to load.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

The issue is just with my profile.  I created a new user and logged into that account and it has sound.

Without deleting my whole profile, how to I fix this?

---

### Post by TechnoJunky on 2018-03-16
It doesn't appear that it was actually VMWare that did this.  Since no one had an answer, I decided to rename my home drive and let Ubuntu create a new one.  I moved the majority of my files from the old directory to the new and all was good, I still had audio, for a while.  I then made some adjustments here and there and once again had no sound.  I did not install VMWare though.  I decided to do a new clean install of Ubuntu although I was sure it was profile specific, I wanted to rule out all else.  After logging in, I still had no sound.  I then renamed my home drive again and created a new, moved files, etc.  This time I did not make adjustments to the audio, which I had previously done.  I believe this was the culprit.  At the time that I installed VMWare I had moved to a different location and was using my laptop without external speakers.  I think it did not switch automatically so I had gone in and under Audio Volume, in the advanced tab, I clicked Automatically switch all running streams when a new output becomes available.  I refrained from doing that this time and still have audio.  If anyone knows what file gets updated when this change is made, I'd like to know so that I can try it again to be sure that's the cause.  But I don't want to do the new profile thing again.  :)

---

### Post by springshades on 2018-03-16
Not a solution because I'm not really sure what is wrong. However, it's another thing to check. On some sound cards that aren't supported very well, KDE (it's probably not specific to KDE) doesn't do a good job of switching between output device options. For example, your laptop speakers vs your audio output jack. Sometimes you can use alsamixer to wander through the various options for various streams in case it gets set incorrectly. I have a machine where I had to write scripts to manually switch between audio outputs using alsactl. In particular, sometimes after updates the various outputs would change their numbering order under the hood, so the scripts would flip what they were pointing at.

There is a slight possibility that something similar is happening on your machine. Particularly if it's a sound card with a dicey driver situation.

---

### Post by TechnoJunky on 2018-03-17
I tested it by creating a new user and the only thing I changed was this setting.  The audio source didn't disappear right away, but I logged out and then back in and the audio source was gone.  So I'd say i found a bug for sure.

---

