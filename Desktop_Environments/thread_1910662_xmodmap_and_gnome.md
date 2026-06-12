---
title: "xmodmap and gnome"
date: 2012-01-17
forum: Desktop Environments
---

### Post by roberto.tomas on 2012-01-17
(with Ubuntu 11.10)

I found an old unanswered thread that has sent me down this path. Almost solved it straight away but there is something weird about startup that is failing.

Here's the problem I'm trying to solve:
Since i quite frequently need to enter numbers in a 1e5 format I want to remap the numlock key to e (so that i can type one-handedly). 
However, i somehow need to activate the number block, so i decided to map Num_Lock on the Scroll_Lock key.

I have a startup application entry I wrote, that just calls xmodmap ~/.Xmodmap
in it, I put the following:
>  remove Lock = Num_Lock
 keysym Num_Lock = Scroll_Lock
 keysym Scroll_Lock = Num_Lock
 add mod2 = Num_Lock
 keycode 77 = e

...then you need to set the numlock in the **on** state by default if you like in the keyboard preferences. Or turn it on/off when you like by pressing Scroll Lock (this will also turn on the scroll lock)

The problem with that is that the numlock key will still turn off the numlock setting if it was on (it does both, outputs the letter and clears the setting). It happens also to not work the other way -- from the off state it stays off. That's odd in itself but, I need to get rid of the  behavior. And I sort of have a solution.

Going to the commandline and running:
> xmodmap -e "remove mod2 = e"
*will* fix it. So I should just add "remove mod2 = e" to my start up script, I would think. But adding that line to .Xmodmap *does not* fix it.

I know the startup script is working because I get the "e"  assigned to the Numlock key. So something is changing the mod2 setting *after* my startup script.

How can I get my startup application to run *after* gnome has finished changing my keyboard settings during startup?

I think that could be considered a bug. Shouldn't anything that happens in a custom startup script happen after any other changes made by the windowing system?

---

### Post by Krytarik on 2012-01-17
First off, I love playing with "xmodmap", at least most of the time, so thanks for giving me the opportunity to do so! :P

Now, off to your solution ;-) :

1.) Modify your ".Xmodmap" to look like this:

~/.Xmodmap:
```
remove mod2 = Num_Lock
keysym Num_Lock = e
keysym Scroll_Lock = Num_Lock
add mod2 = Num_Lock
```2.) From your "Startup Applications", remove/disable the item you've previously set up for calling it per command; as long as it's named either ".Xmodmap" or ".xmodmap", it should be called automatically upon login, and in turn you don't need to override the default keymap yourself, thus no conflicts and no delay crap or such.

Regards.

---

### Post by roberto.tomas on 2012-02-24
Krytarik, I never noticed your response. Thank you for writing it. :)

After following your solution:

Scroll Lock is now really Num Lock, and not also Scroll Lock.

I had to turn off the "default numeric keypad keys" to get it to start with the numlock in the on position (ie, with numbers resulting frm the numpad). This is the opposite of before, and opposite the intuitive sense of things -- any idea why?

Num Lock is now nothing but "e". :)

Any idea why the old setup worked, *except* for the removal of mod2 at the end?

Im not sure if I should file a bug or what for the numeric keypad keys thing... but applying your solution today made me wish I'd seen it earlier.

---

### Post by Krytarik on 2012-02-24
> **roberto.tomas said:**
> Any idea why the old setup worked, *except* for the removal of mod2 at the end?
Well, your setup was so weird that I don't even want to *begin* to imagine what everything was doing, once again. :D

> **roberto.tomas said:**
> I had to turn off the "default numeric keypad keys" to get it to start with the numlock in the on position (ie, with numbers resulting frm the numpad). This is the opposite of before, and opposite the intuitive sense of things -- any idea why?
Actually, the option "Default numeric keypad keys" controls the mapping of all keypad keys - incl. NumLock - rather than the NumLock state itself. And since we have remapped NumLock to ScrollLock, it seems like these are conflicting.

---

