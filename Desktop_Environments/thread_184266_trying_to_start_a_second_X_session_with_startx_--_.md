---
title: "trying to start a second X session with startx -- :1 - getting kicked out"
date: 2006-05-29
forum: Desktop Environments
---

### Post by ponkan on 2006-05-29
I'm trying to start a second X session by typing "startx -- :1" at an xterm; What happens is that I get the gray background with the "X" cursor for a few seconds, then I'm booted out and back into my current session. Sometimes the new session sticks around for a few minutes -- gray background and black X cursor, nothing loads. Going back to terminal 7 shows the xterm with a series of lines similar to this:
```
AUDIT: Tue May 30 03:44:04 2006: 10553 X: client 1 rejected from localhost
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified
```

A new set appears every few seconds, until the process gives up. Looking at the Xorg.1.log files for the two cases doesn't reveal any differences aside that the latter case has a long string of "client 1 rejected from localhost" lines.

I was able to start the second session once, but that was a long time ago. I'd be grateful if someone could point out possible ways to diagnose/solve this problem, short of reinstalling the whole X server -- which I might eventually do anyway. Google results on the output mostly pointed to people trying remote connections running into issues with .Xauthority, but I can already log into the first display.

EDIT: this is under breezy

---

