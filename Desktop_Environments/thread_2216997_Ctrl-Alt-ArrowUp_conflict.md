---
title: "Ctrl-Alt-ArrowUp conflict?"
date: 2014-04-15
forum: Desktop Environments
---

### Post by k999 on 2014-04-15
Hi,

I seem to have a keyboard shortcut conflict on my system. I change viewports with Ctrl-Alt-Arrow, and that works fine except Ctrl-Alt-ArrowUp which sometimes works immediately, but sometimes I just have to hit it up to 5-10 times before it responds. My best hypothesis so far is that multiple actions may be set up for the same keycombo, so that sometimes the keycombo is hijacked by the other action (which doesn't do anything that I can see). I think this happened after a colleague tried to help me get some more sane defaults in unity a long time ago, and that ended up with us running ccsm and playing around a bit. I'm not sure we were able to reset everything back to how it was. I have since upgraded Ubuntu (which didn't help), and last week I went through a lot of settings in dconf-editor to change all keyboard shortcuts back to their defaults, but nothing has worked so far. 

How do I start from a keycombo and find out what actions are linked to it? Like some kind of "search for actions" based on keycombo. If I could do that, it should be easy to see what is wrong.

My keyboard works fine, by the way, there's nothing wrong with my ArrowUp key.

---

### Post by grahammechanical on 2014-04-15
If you are using 13.10 I would say go to System Settings>Keyboard>Shortcuts tab and see what key combinations are enabled or disabled. There most likely is something similar in Ubuntu 12.04.

Regards.

---

### Post by k999 on 2014-04-15
I'm on 13.10. Interestingly, I tried disabling "Switch to workspace above" under Settings>Keyboard>Shortcuts>Navigation, which showed Ctrl+Alt+Up. Now I can't set it back! I can set it to Ctrl+Up or Alt+Up, but whenever I click Ctrl+Alt+Up it just reverts to "Disabled". Something very fishy is going on.... Is there some way to reset all keyboard shortcuts and just start over?

---

### Post by k999 on 2014-04-15
Hmm, I actually managed to set it (finally) by hitting Alt then Ctrl then Up, but if I press Ctrl then Alt then Up, it just reverts to Disabled. I always hit Ctrl then Alt then Up, by habit. My poor laptop is apparently supersensitive to the order. Changing the order didn't help when changing workspace with the keycombo though...

---

