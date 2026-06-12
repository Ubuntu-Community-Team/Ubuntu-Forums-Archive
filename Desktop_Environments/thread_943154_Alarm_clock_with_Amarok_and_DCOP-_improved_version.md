---
title: "Alarm clock with Amarok and DCOP- improved version"
date: 2008-10-09
forum: Desktop Environments
---

### Post by DJ Wings on 2008-10-09
While searching for ways to set up an alarm clock, I came across [this thread](http://ubuntuforums.org/showthread.php?t=57535). Of course, there hasn't been much activity for the past three years, so I thought I'd dig this idea up again. This is what I was able to come up with after a few minutes of fooling around with DCOP, using the original code as a starting point:
```
amarok ~/wakeup.m3u
dcop amarok player stop
dcop amarok player enableRandomMode 1
dcop amarok player setVolume 100
dcop amarok player next
dcop amarok player play
dcop amarok playlist setStopAfterCurrent 1
```
If all goes well, it should load a playlist called "wakeup.m3u" (in my case, one loaded with Swedish death metal :guitar: ), picks a random song after setting the volume as high as it'll go, and plays it all the way through- then stops.
There's one minor bug: Since Amarok plays files it loads via the command line automatically (is there a way around this?), the first track on the playlist will be played for a second or so, then skipped promptly. If you have a scoring script turned on, don't expect it to be at 98 anymore after a few weeks of this...
What do you think? The script can be run through Cron or another scheduling tool (the original thread mentioned KAlarm).

---

### Post by p_quarles on 2008-10-09
> **DJ Wings said:**
> There's one minor bug: Since Amarok plays files it loads via the command line automatically (is there a way around this?), the first track on the playlist will be played for a second or so, then skipped promptly. If you have a scoring script turned on, don't expect it to be at 98 anymore after a few weeks of this...
I would try working with the -e/--enqueue argument -- that seems as though it would load files without assuming that they are to be immediately played.

---

### Post by DJ Wings on 2008-10-10
> **p_quarles said:**
> I would try working with the -e/--enqueue argument -- that seems as though it would load files without assuming that they are to be immediately played.

The problem is that -e adds the playlist to the existing one, which means that after a while, the existing playlist will be pretty cluttered.
Here's my suggestion:
```
amarok -e ~/wakeup.m3u
dcop amarok playlist clearPlaylist
dcop amarok queueMedia ~/wakeup.m3u
dcop amarok player enableRandomMode 1
dcop amarok player setVolume 100
dcop amarok player next
dcop amarok player play
dcop amarok playlist setStopAfterCurrent 1
```
A bit sloppy, but it works.

---

