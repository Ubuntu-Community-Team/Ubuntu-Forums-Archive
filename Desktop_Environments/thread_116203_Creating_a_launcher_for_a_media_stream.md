---
title: "Creating a launcher for a media stream?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by TeeAhr1 on 2006-01-12
Why, you ask?  Who cares?  Just to do it, really.

Let's say my college station is [http://999.999.99.9:8502/stream.pls](http://999.999.99.9:8502/stream.pls)  When I use the gnome-open command, it tries to open in Firefox because it sees the http; not what I'm trying to get at, obviously.  Then I tried "rhythmbox [http://blah](http://blah) blah blah"  That didn't work, it hangs Rhythmbox when it tries to open.  Anyone know the right syntax for this?

---

### Post by SickTwist on 2006-01-12
You could save the stream.pls file on your computer then create a launcher for xmms or beep-media-player to open the local file.

E.g.:
beep-media-player /home/jsixpack/stream.pls

Not optimal but it does work.

---

