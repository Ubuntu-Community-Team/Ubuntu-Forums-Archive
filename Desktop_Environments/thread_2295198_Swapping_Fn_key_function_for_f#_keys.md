---
title: "Swapping Fn key function for f# keys"
date: 2015-09-16
forum: Desktop Environments
---

### Post by Copper Bezel on 2015-09-16
I've poked around a bit on this, but is there a simple way to reassign the function keys (in my case, f5-12) to work as they do on a Mac, where Fn+key sends f# and the key without Fn sends the brightness, trackpad, audio etc. signal? The machine is an Asus compact laptop running Ubuntu 15.04.

It kinda seems like there should be a simple way to do this that doesn't involve clunky scripts at startup that sometimes work until the machine is suspended and so on, based on things like xmodmap that are likely to be deprecated, and so on. I *definitely* don't want to change the keybindings in the OS to trigger volume control and things, because that means assigning the f# keys to those tasks permanently, while some apps still do use them as accels for things. I'd really like to just be able to reassign which signal is being received at as deep a level of abstraction as possible. I *really* want to at least swap the audio and brightness ones, but I've noticed that the brightness buttons don't actually send normal keypresses and use something called rrnotify I've never even heard of. = / 

Any ideas? Is there an obvious solution I'm overlooking?

---

### Post by Copper Bezel on 2015-09-17
I guess I'm bumping, but to clarify, I know that the Fn key isn't a modifier key, and that when I'm hitting Fn + F10 or whatnot, the keyboard hardware itself is sending "Audio mute", which is different from Alt or Shift or Super, where the OS sees modifier keydown, keypress, modifier keyup and can interpret that however it's set to do so, and of course that the F# keys that those hardware-related buttons happen to be combined with are arbitrary and differ between keyboards. So what I really need is a way to permanently, persistently switch the keycodes received for each of those individual keys arbitrarily. But I'm wary of using xmodmap for that, since it's always been a little unpredictable for me, and I kinda wish I knew what this rrnotify thing was and whether I can even assign those events from xmodmap.

---

### Post by Copper Bezel on 2015-09-21
I really hate to bump like this, but can someone confirm for me whether or not I'm looking at the right set of tools, and if there is no obvious solution, tell me so?

---

