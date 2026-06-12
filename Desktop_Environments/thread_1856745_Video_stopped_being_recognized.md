---
title: "Video stopped being recognized"
date: 2011-10-08
forum: Desktop Environments
---

### Post by rdbowers on 2011-10-08
In order to try to fix an audio problem I'd been having, I tried installing ALSA-OSS (interfacing module) on my desktop system.  In the middle of the install, the computer crashed - locked up.

Now I can't get 10.04LTS to properly start.  I get a message that the video and other settings need to be set and cannot be determined.  I've tried everything I know to do - checked the X11 settings, tried to start in a lower resolution (no luck - it just keeps going back to "run in a lower resolution"), trying to undo the changes I'd made... nothing seems to help me get past the headache.

When I get into the X11 drive, I noticed that the .config file wasn't there... there was several .config.backup_XXXX... files, and they all looked the same.  When I copied one of them to XXXX.config (I'm on my wXP partition and can't remember the name) and rebooted, it vanished.

I'm running a homebrew Intel dual core 3.4ghz, Intel motherboard with built in sound, Creative audigy II, ethernet, Nvidia GeForce 210, 4gb ram, plus several USB devices (including a USB sound card and microscope camera).  

I really don't want to reinstall, and would prefer to stay with 10.04lts until I have to go to the next upgrade.  I have a lot of important software installed and don't want to loose it all and spend a couple of days re-installing everything (even some proprietary and hard-to-find stuff).   I think if I could figure out what happened, I may be able to go in and fix it.  But I could use some help!

Bob

---

