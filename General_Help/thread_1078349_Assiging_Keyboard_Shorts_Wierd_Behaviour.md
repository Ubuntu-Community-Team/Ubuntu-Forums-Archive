---
title: "Assiging Keyboard Shorts: Wierd Behaviour"
date: 2009-02-23
forum: General Help
---

### Post by kneewax on 2009-02-23
Hi Folks,

Ubuntu: Intrepid 64bit
Nvidia Graphics Driver 173 on integrated Nvidia Display adapter

Here is a problem that is just wierd!

I really want to assign a shortkey on the 'Super' key for each of Volume Up, Volume Down, and Volume Mute.

I tried doing this in System>Preferences>Keyboard Shortcuts.

So far so good, but two things now happen.  Firstly when I try to enter a key combination for these functions it will only accept the stroke of the super key so it assigns 'Super L' to the function not 'Super + <key>) Secondly, the moment I try to assign any key stroke my whole system theme flips into 'negative'  (Please see screenshots).  I've had no other issues with display settings, so it does seem to be a problem being caused by this particular utility.

Anyone know what on earth is going on here?

[Edit: Added screenshots]

---

### Post by sirjoebob on 2009-02-23
> the moment I try to assign any key stroke my whole system theme flips into 'negative'

Sounds like you have compiz enabled. Flip over to the compiz config settings manager and disable the negative plugin or at least change the keyboard shortcut for it. Ubuntu's shortcut manager does not see conflicts with the ccsm shortcuts.

---

### Post by kneewax on 2009-02-23
Now that bit was was embarrassingly easy to fix! I didn't even know I had negativce window enabled!  Thanks sirjoebob!

---

### Post by sirjoebob on 2009-02-23
NP. I only knew the solution because I did the same thing once.

---

