---
title: "Window resize very slow, everything else ok."
date: 2006-09-06
forum: Desktop Environments
---

### Post by IceNine451 on 2006-09-06
This is my first foray into full blown linux (I've played with Fedora and Breezy in the past a little bit), but this is my first attempt to move completely over. Anyway, I have my nVidia drivers all installed ok (I think, is there any real good way to know if they are working properly or not?) along with XGL and Compiz all installed and working ok. All the effects seem to be working fine (eg. window wobble, 3d virtual desktop switching etc...) and everything seems to be working as it should, all accelerated and such except for the window resize. Whenever I resize a window by grabbing a corner/side or using the right-click resize command, it goes very slowly and my CPU spikes to 100%. No other moves I can find seem to do this, just resizing doesn't seem to be accelerated for some reason. Any clues on how I can fix this would be most appreciated.

---

### Post by bulldog on 2006-09-06
You could type "csm" in your terminal and see if you can alter some settings.

It's all beta and there will be some bugs in it.

Just fool around a little with the settings menu but don't make to many changes at once.

---

### Post by d3k4y on 2006-10-29
Just in case anyone finds this post while looking for an answer.  If you open Beryl settings manager, go in the section "Resize windows" and change Resize Display Mode to Stretch or something else, you can resize windows without killing the cpu or get that laggy look.  Stretch doesn't look as cool as the normal mode where the window is all wiggly, but its better than the broken, slow look.

I had this working in beryl 0.1, but in beryl 0.1.1, I cannot get the normal resize effect to work.  If anyone, does find the answer to getting normal resize to work, please let us know.  (x1600, dapper & edgy, fglrx of course)

---

