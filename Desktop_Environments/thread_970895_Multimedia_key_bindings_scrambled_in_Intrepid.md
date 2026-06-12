---
title: "Multimedia key bindings scrambled in Intrepid"
date: 2008-11-04
forum: Desktop Environments
---

### Post by Nesnej Trick on 2008-11-04
Today I upgraded Kubuntu to Intrepid Ibex and after getting to the desktop (no minor feat, but let's not go into that) I wanted to listen to some music. I hit the Play/Pause key on my keyboard... and nothing happened.

So, I started my detective work. Keytouch and its associated daemon keytouchd was running and the conf file was intact, so that didn't seem to be the problem.

I fired up xev to see what key codes I would get when going through the keys. To my surprise I discovered that the multimedia keys appear to have *several* bindings, most of them quite bizarre. E.g. the Media key registers simultaneously as "XF86AudioMedia", "Alt_L" and "right". Play/Pause gets registered as "XF86AudioPause", "Ctrl_L" and "s". Most programmes hence interpret the Play/Pause key as "Ctrl+S", which is mildly put annoying.:mad:

My keyboard is a Logitech Internet Navigator and the selected layout is Swedish-nodeadkeys. The question is, how do I get the Multimedia keys to register as XF86[something] only in KDE?

---

