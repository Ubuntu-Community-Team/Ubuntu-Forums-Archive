---
title: "splash screen background"
date: 2007-03-20
forum: Desktop Environments
---

### Post by josephus on 2007-03-20
I'm using Edgy Eft, with gnome desktop and I'm having trouble changing the splash screen background colour that shows up between login and desktop showing up.  It's currently grey and I would prefer for it to be black, and the grey shows up whether or not I have the splash screen image set.

I've tried changing the background colour in the Login Window Preferences, but that color only shows up for a second before changing back to grey again.

I've changed the desktop background colours to make sure that I wasn't seeing that.  I'm not sure which setting to play with next.

---

### Post by josephus on 2007-03-20
I think that my X server is somehow set to a grey background and that's what I'm seeing.  Anyone know how I change it back to black?

---

### Post by josephus on 2007-03-21
solved the problem.  in case anyone runs into a similar problem, it ended up being the fact that i was using xfwm4 with compositor enabled, which has gray as a default background.  i don't know how to control the background color in the config files, so i ended up recompiling after changing the source code.  complicated solution to a simple problem.

---

