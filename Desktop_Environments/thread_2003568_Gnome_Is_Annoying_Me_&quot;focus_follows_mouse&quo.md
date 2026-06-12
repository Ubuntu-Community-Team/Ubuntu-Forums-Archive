---
title: "Gnome Is Annoying Me: &quot;focus follows mouse&quot; Not Working"
date: 2012-06-14
forum: Desktop Environments
---

### Post by JSeymour on 2012-06-14
G'day,

I've got Ubuntu 10.04 LTS (Lucid Lynx) installed on both my work laptop (a Dell Latitude D530) and my desktop/server at home (a Dell PowerEdge 1600SC server).  Running the Gnome desktop on each.  Running dual-head on each.  (A pair of 19" flatscreen monitors, driven by an ATI Radeon graphics adapter.  The laptop's built-in display and a 19" LCD flatscreen at work.)

Coming from a Sun background, I'm used to "focus follows mouse."  It works on my machine at home, but it's not working on my work laptop and it's driving me crazy.  It's only a matter of time before an errant keypress turns out to be more than an annoyance.

I've tried everything I can find on the 'net/web to persuade Gnome on my work laptop to behave itself, to no avail.  Anybody have any clues as to why it's not doing as it's told?

Thanks,
Jim

---

### Post by JSeymour on 2012-06-19
Problem solved.  Misfire on my part.  I'd gone into Settings -> Preferences -> Appearance -> Visual Effects and selected "Normal" at some point.  Little did I know that replaced the metacity window manager with Compiz.  Once I thought "Hmmm... focus is a wm thing, not a desktop thing" and did some research, I figured it out.

Changing the appearance back to "None" (which put metacity back) fixed the problem.  Putting appearance back to "Normal," then making the appropriate changes with Preferences -> CompizConfig Settings Manager also fixed it.

Jim

---

