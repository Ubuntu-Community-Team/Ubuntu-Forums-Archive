---
title: "[SOLVED] X crashes when switching displays in Gutsy"
date: 2008-01-20
forum: Desktop Environments
---

### Post by x1a4 on 2008-01-20
Hi,

On Gutsy, sometimes (seemingly at random) when I switch displays--whether it's from one X session to another or from X to a console--the X session I'm switching from crashes and restarts on another VT, closing all open applications in that session and forcing me to re-login.  

How can I diagnose and fix this very annoying problem?  Is it related to the recent xorg update?

Thank you.

---

### Post by x1a4 on 2008-01-26
I don't know what the problem was but it seemed to only be happening when DosBox was running so I solved this (sort of) by exiting DosBox when switching displays. I also told GDM which VT to start each x session so that when X crashes, I log out, or hit Ctrl+Alt+Backspace it will restart on the same VT.

---

