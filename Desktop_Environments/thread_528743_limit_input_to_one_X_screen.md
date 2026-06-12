---
title: "limit input to one X screen?"
date: 2007-08-18
forum: Desktop Environments
---

### Post by drummingpariah on 2007-08-18
I've been scouring the forums and google for the past hour, trying to find a way to get my wacom to function in a workable state.  I've got it running, everything's peachy and I've got a nice sensitive stylus..

but I have two screens.  Basically, what this means is that it works great as a mouse cursor across the two screens (set up as two separate X sessions sharing all input devices, no Xinerama, no Twinview).  When I open up the GIMP, for example, the input is mapped relative to the total screen size (from both screens) so placing the wacom pen in the middle of the tablet places the X cursor in between the two screens, and the GIMP cursor right in the middle of the image I'm working on.  This is no good, because if I move 1 pixel over toward the screen not running the GIMP, focus is taken away and I'm creating a boundary box on my desktop (or deleting things, or launching who-knows-what because GIMP no longer has focus).

I'm wondering if anyone's familiar enough with the way nvidia-settings configures two screens (again, not using Xinerama or Twinview) and how it maps the input from devices.  I'd be perfectly happy to have the wacom only recognize one X session as its own, and have my mouse span both X sessions.  If I were using a second machine, I could simply plug the wacom into that second machine, set up Synergy (so the wacom ONLY gives input that that second machine) and I'd be a happy camper.  If anyone can offer any insight or further advice, I'd really appreciate it.  This is maddening.

---

### Post by ac7ss on 2008-01-13
I believe you are talking about SCREENS not SESSIONS. Screens are the same X session spread over multiple desktops. SESSIONS are often for different users. But I have no help for your multiple screen problem.

---

