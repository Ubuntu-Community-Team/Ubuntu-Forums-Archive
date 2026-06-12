---
title: "Two screens: Problems with Desktop background and vino"
date: 2009-11-26
forum: Desktop Environments
---

### Post by waltersch on 2009-11-26
Hi,

the two problems may have an identical cause. When I only configure a single screen with 1280x1024, they don't occur.


Ubuntu 9.04 normal installation with gnome.

screen 1: flatscreen 1280x1024 (DVI-D)

screen 2: flatscreen 1024x768 (VGA), logical position at the right side of the 1st screen.



1st problem:

During a remote connection to vino on the ubuntu PC with the two screens, vino gives only an area of 1024x768 as virtual resolution on the remote PC, that is the top left part of screen 1. With the remote mouse, I can't go over the whole 1280x1024 desktop. Working on the ubuntu PC at the same time is fine; the mouse goes over the whole area and both panels are fully accessible.



2nd problem (appears with or without remote control via vino):

After login, the desktop background pattern fills only an area of 1024x768 (from top left) on the 1st screen. The top and bottom panel work fine over the whole width of the screen. When I drag a window
over the screen, it leaves traces on the areas without background pattern, that is on the right and bottom side of the 1st screen and on the whole 2nd screen (traces are similar to the success screen of the game solitaire). Eventually (after some minutes), the whole 1280x1024 desktop background is filled with the background pattern, which then consists of pieces 1024x768.


An Update to 9.10 would only be an option if these problems are documented and definitely solved in 9.10. Reason: Before I connected the 2nd screen, I tried 9.10, but got a dead audio (no solution after 5 hours) and a dead DVB card (2 problems, only one could be solved). Thus I went back to 9.04 from scratch.

My first aim is a solution for both problems. If this has proven as impossible, I would try a solution that only solves the 1st problem (like using vncserver).

Meanwhile, with some testing, I found a way to work around both problems: The logical position of screen 2 must be bottom-aligned with screen 1 (not top-aligned like I did it first). Then, both problems do not occur, and vino gives the whole 1280x1024 area of screen 1 for remote control.
I will not yet mark this thread as solved, because it is still a problem if you can't arrange two screens as you want.

Thanks!


Walter

---

