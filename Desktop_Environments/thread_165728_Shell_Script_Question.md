---
title: "Shell Script Question"
date: 2006-04-25
forum: Desktop Environments
---

### Post by Mastus on 2006-04-25
Is it anyway possible to make a shell script that automatically would paste clipboard contents to current window.

I'm trying to make a Amarok/Gaim "now playing" script. So far I have managed to get the track info from Amarok via dcop, and set it to clipboard (again via dcop). Script can be started via Katapult.

So far: Alt+Space -> write "np" -> paste text

---

### Post by aysiu on 2006-04-25
Doesn't AmaroK already have a "now playing" feature called OSD?

---

### Post by Mastus on 2006-04-25
Yes it has OSD, but what's the use in IRC ;) 

Well, I managed to get a satisfying solution: New quick launch icon, which launches this script: 

dcop klipper klipper setClipboardContents "np: `dcop amarok player artist` - [`dcop amarok player album` #`dcop amarok player track`] `dcop amarok player title` [`dcop amarok player totalTime`] @`dcop amarok player bitrate`"

I just have to push middle mouse button then...

Thanks for bearing with me.

---

