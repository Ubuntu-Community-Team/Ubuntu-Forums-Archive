---
title: "Dvorak"
date: 2005-05-29
forum: Desktop Environments
---

### Post by Spug on 2005-05-29
I decided to test out Dvorak, so I swapped the physical keys to Dvorak (Norwegian version, as I'm from Norway and have a Norwegian QWERTY keyboard). I also added the Dvorak Norwegian keymap to Gnome and set a toggle key, so I can use them both interchangably, depending on if I need to get some typing done fast or am in the mood to learn more Dvorak.

Some keyboard shortcuts still use the Qwerty map when I use Dvorak, though. When I press Alt+V in gnome-terminal, for example, the View menu opens like it should, but it also opens that menu if I press Alt+K (which is located where the V is in QWERTY). How comes?

So, I wonder what I should do about shortcuts. The Gnome ones would have to be fixed somehow, and the ones I use the most are screen's and irssi's, I guess. They're customizable, so should I change them to the Qwerty locations? ("^A E" would then be "detach" in screen (instead of "^A D"), which makes no sense but is easily accessible.) Or let the letter count more than location? (Of course, many keyboard shortcuts are designed for qwerty. Pretty much all, but there are some that are worse than others; xmms's "zxcvb", for example. That's sucky.)

In addition, I wonder what I should do with the ttys. "sudo loadkeys dvorak" loads the standard US Dvorak keymap, which is good, but it would be even better if there was some way to load the NORWEGIAN Dvorak keymap like this. There's no equivalent .kmap.gz file for the dvorak-no layout, even though Gnome's keyboard preferences had it.

---

### Post by Spug on 2005-05-30
Okay, I found a no-dvorak.map.gz file, at least.

---

