---
title: "Ubuntu media applications for a NAS environment"
date: 2006-01-23
forum: Desktop Environments
---

### Post by bjhess on 2006-01-23
I am in the process of building a NAS and archiving my entire music and movie collection to hard disk.  The bulk of my viewing will be through a modded Xbox and XBMC.  There is potential in the future to build a traditional computer-based client, but all I want right now is to be able to somewhat conveniently consume my media on my existing computers as well as the Xbox.

I have searched for answers to my questions on Google as well as at this forum directly.  I've found lots of information, but I haven't really found a thread specifically discussing my desired usage.  The information is all over the place; decentralized.

So I will split out my questions based on process:

**Build a NAS**

I'm fairly happy with my direction here.  I've spent a lot of time focusing on data storage configuration and my symlink farm to centralize data access.  I don't really have any questions at this point in time.  I've been happy with Ubuntu server in this realm.

**Rip to NAS**

I'm actually *approaching* happy with Linux's performance here.

For audio ripping it appears that grip is a pretty darn functional tool.  After setting it up, ripping to FLAC is a breeze in all but the cases where the online DB does not contain the target CD.  I'll accept any comments on this configuration, but I don't have any obvious questions.

I do not plan on transcoding my DVD rips.  I just want to quickly and conveniently rip my discs and be done with it.  I have two scenarios that I want to target: ripping an entire DVD and ripping just the feature from the DVD.  When ripping an entire DVD, I'd like the menus to remain intact.  When ripping just the feature I want to be sure that the chapter stops are available for speedy navigation.

I messed with dvd::rip and some other apps, but strangely the most user friendly utility I found was the simple dvdbackup command line utility.  With options to backup the entire disc or just the feature and to specify the name of the resulting movie directory, I was really happy.  Two problems: I'd prefer the files to be created in the base directory, not a VIDEO_TS folder and rips took between 45 and 75 minutes.  The first issue I suspect will make starting a movie in XBMC a little more annoying, though I could possibly build a script to create symlinks in order to make things more convenient.  The much bigger hurdle will be rip duration.

*Does anyone know how to speed up rip duration using dvdbackup?*

**Playing media**

I will not address the audio concerns as of yet.  I really like iTunes, but the decision to go with FLAC is really going to throw my choices up in the air.  If a playback utility also conveniently incorporated podcasts, I'd probably be fine.

I attempted to play video files ripped to my NAS with ogle and xine, which both support menus.  Ogle seemed nice and simple, but crashed my machine twice in ten minutes.  No dice.  Xine seems OK, but I'm not sure how to go about playing hard-drive-based files.  I'd like to select the base IFO file because that should get me my menus and chapter stops.  Unfortunately I can't do this (or don't know how).

*What method do you use for Linux DVD playback with menu support and/or how do you play ripped DVD's with xine?*

**Ultimately**

The more I familiarize myself with Linux/Ubuntu, the more I'd like to move all of my machines (a ripping machine, laptop and workstation) to Ubuntu, dual booting when necessary.  Unfortunately, as you can see, there are a couple hurdles I need to jump in order to make this possible.  Thanks for any help you can provide!

Barry

---

### Post by bjhess on 2006-01-24
Bump to ping the group.

---

