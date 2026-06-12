---
title: "Random text gets inserted into textboxes."
date: 2009-06-13
forum: General Help
---

### Post by Coder543 on 2009-06-13
On my mom's Ubuntu 9.04 laptop, she'll be typing along inside of firefox, and it randomly inserts chunks of text from anywhere. It is very frustrating, and makes no sense. Does anyone else experience this or have a solution?

---

### Post by jenkinbr on 2009-06-13
Does she per chance accidentally hit the middle mouse button on the laptop while typing?

The middle mouse button defaults to pasteing the current selection in ubuntu, even if that selection is in a different window.

---

### Post by Coder543 on 2009-06-13
well, its a laptop... it doesn't have a middle mouse button, and she's definitely not pressing both buttons at once.

---

### Post by QIII on 2009-06-13
If you use her machine for a while, do you run into the same behavior?

Does she have any Assistive Technologies set?

I'm not trying to be smart.  I'm a bit of an old fart, and just having bifocals is a PITA sometimes.

---

### Post by Coder543 on 2009-06-13
Well, i have my own machine that I use, but i've watched it happen. I'm sure that assistive technologies are turned off (according to the assistive technology boxes).

---

### Post by QIII on 2009-06-13
Have you actually used her machine for a while to see if it happens to you?  

Sometimes a person's hand position or typing habits can cause what look like strange effects.  Hitting the Ctrl key by accident instead of the Shift key, for instance.

Since I never make mistakes myself, I always blame it on a defective keyboard...

It may not be even close to the answer, but it does fit into the "what, exactly, were you doing when you encountered this behavior" part of the problem solving process.

---

### Post by Coder543 on 2009-06-13
lol, ok

---

### Post by Confuseling on 2009-06-13
If it's mostly in firefox, try typing about:config in the address bar, then autoscroll in the filter. Set to true.

If that doesn't work (of if autoscroll annoys her too), set autoscroll back to false, type 'middlemouse' in the filter, and set middlemouse.contentLoadURL, middlemouse.paste and middlemouse.openNewWindow to false.

---

