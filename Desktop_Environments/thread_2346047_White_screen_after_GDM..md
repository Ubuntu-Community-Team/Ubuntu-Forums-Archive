---
title: "White screen after GDM."
date: 2016-12-10
forum: Desktop Environments
---

### Post by hickscorp on 2016-12-10
Good evening!

I've been a user of XFCE 4 for a while. Recently, I wanted to give a shot to GNOME 3. I installed Ubuntu Gnome 16.10.
At first, everything was running as expected. But after updating the system, I get a white screen (With functionnal mouse pointer) after logging in using GDM.
What's weird is that if I use a tty and issue `startx` directly, my desktop session starts without problem.

Is there anyone with the same or a similar problem, and ideas about how to solve it?
Thanks!
Doodloo.

---

### Post by hickscorp on 2016-12-12
Replying to my own question... It was a silly mistake. As I was before using XFCE, I had set up a way for Compton as a compositor by running it upon X startup. To do this, I had a `~/.xprofile` file in my home folder containing `compton -b`. This file clearly makes Ubuntu GNOME fail to start when started with GDM.

Cheers,
Doodloo.

---

