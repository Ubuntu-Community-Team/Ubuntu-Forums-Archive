---
title: "MythTV / MPlayer problem"
date: 2006-01-02
forum: Desktop Environments
---

### Post by timd on 2006-01-02
Hi all, my first post here, so please be gentle! (Apologies if this is in the wrong place too!) :)

I've just installed and setup MythTV on my Dell, following the various HOW-TO guides on this site and others. At the moment it's only able to play back existing video and audio files as this was a prove-out before buying the TV cards etc to rebuild an old PC into a MythTV media centre.

All seemed to be going well, I can login to my mythtv login and run mythfrontend and all works fine.
The problems start when I add mythfrontend to the .xsession file to make myth auto-start when logging in. When it's set like this Myth starts, and seems to work ok, until I select a video file to playback. Once the file is started the keyboard becomes non-responsive. Nothing works. At this point all I can do is press the power button as the video just cycles around and around with no way of stopping it or returning to Myth.
I'm using the default of MPlayer to playback the files.

Some further searching leads me to think that this is a window focus issue - I've tried installing alternative window managers, but the problem persists.

Has anyone else experienced this problem, or know of a cure?

Help!! :)

---

### Post by timd on 2006-01-02
Ah, fixed it using openbox and .xinitrc info from [https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession"), thought I'd reply to myself in case it helps anyone else. :)

---

