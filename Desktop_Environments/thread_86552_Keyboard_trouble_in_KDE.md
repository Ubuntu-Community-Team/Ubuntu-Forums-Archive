---
title: "Keyboard trouble in KDE"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Calle on 2005-11-05
My HP Pavilion ze2000 series laptop is now installed with Ubuntu 5.10, though I meet this problem:
Wherever I are, whatever I do in KDE (Kubuntu) the characters I enter from the keyboard get real disturbed in action. 
Example:
I physically type > the quick brown fox but with random instance the computer messes it up to be something like this: 
> theee qquickkk    broooown foxxxxxxxx
(it also happens with whitespaces and all other characters on the keyboard)

This problem does **not** occur when using Gnome on the excact same computer.

My xorg.conf can be found [here]("http://pastebin.com/418708")

---

### Post by shinygerbil on 2005-11-05
I'm guessing you've checked out the keyboard options in System Settings (i.e. keyboard repeat rate etc). If you haven't, definitely look into it (System Settings -> Keyboard).

Otherwise, I don't know of a solution, but I wouldn't think it was to do with xorg.conf - this is shared between the two desktops, unless you have them installed separately of course.

Steve

---

### Post by Calle on 2005-11-05
Ah thank you, something is not working in my brain. Of course I hadn't checked for any "keyboard repeat" in the settings. 
(though, I can't see why this was enabled from my default installation)

---

