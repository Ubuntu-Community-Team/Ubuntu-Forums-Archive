---
title: "gtkpod problems"
date: 2006-03-28
forum: Desktop Environments
---

### Post by vladuz976 on 2006-03-28
when i try to sync in gtkpod, i get a permissions error. what could be wrong?

---

### Post by Edward The Bonobo on 2006-03-28
> ...what could be wrong?

In short...gtkpod.  It's a flaky package.  I've been using it for a few months and have got kinda used to some of its quirks.  But it's a bit dire.  Some things I've learned along the way:

[LIST=1]
[*]It really helps to have the latest version of gtkpod you can find.  I think the one in the Breezy repositories is still 0.94.  Somewhere in the forums (try a search) there's instructions on how to grab and install v0.99.2 or even maybe v0.99.3.
[*]The first time you use your iPod, you have to start with iTunes.  Add at least one song.  Thereafter, gtkpod might - *might *- work.
[*]If it doesn't Synch, try unplugging your iPod.  Yes, it will be displaying 'Do not disconnect' - but it doesn't seem to do any harm.  Plug it in again.  Wait for it mount and the browser to pop up (assuming you have automount enabled), then try synching again.  Sometimes it will complete most of the synch and then give an error.  Repeat until it gets it right.
[*]Oftentimes you get tracks which *appear *to be loaded on your iPod, but when you play them, it just skips on to the next track.  Delete these and re-load individually.  It seems to work better if you load them one by one as files, rather than adding a directory.  Maybe.
[*]There is a user manual (of sorts) on the main gtkpod site, but a) It seems to relate to later versions and b) it is in hideous .txt format.  I've done a bit of a typography job on it - but I haven't got a convenient space to host it. (would anyone like to offer some?)
[/LIST]

I hear that Banshee works better for synching iPods - but the version in the repository is old and doesn't have the synch facility.  I'd been waiting for the Dapper release, but now that's been delayed, I may investigate installing it.  Amarok also works, apparently.

Enjoy!

---

