---
title: "gnome panels permanently hidden?"
date: 2010-07-30
forum: Desktop Environments
---

### Post by decomp on 2010-07-30
Hi all,

So in gnome, I create a new panel, set it to the left or right side, and disable expand. Then I open gconf-editor and adjust the key '/apps/panel/toplevels/panel_2/hide_delay' (as well as unhide delay) to a value of 0 - as well as disable animations for the panel so that it will open and close instantly. That's how I like it :) 

But now every time I reboot the panel is permanently hidden and won't respond to mouse over. To get it to show again I have to change one of it's values in gconf. then it will show again and behave as normally.

Any ideas how to make it show normally?

---

### Post by hariks0 on 2010-07-31
Change the settings in Ubuntu Tweak.
:popcorn:

---

### Post by decomp on 2010-07-31
Hi hariks0, 

adjusting 'enable panel animations' in ubuntu tweak had no effect - on panel animations, or on the panel's visibility. I've tried deleting and recreating the panels with no change, except that now I find I have a 'phantom' panel known as panel_1 which I can not force to appear in any way, and therefore cannot remove. 

So add to original question, 'how do I delete a panel I can't see?'

Thanks! :)

---

### Post by Ginsu543 on 2010-08-01
I had exactly the same problem as you. I had panel animations turned off using gconf-editor, which worked fine under Karmic. It worked when I first installed Lucid. But after one of the system updates, it no longer worked. Like you, the panel would disappear upon reboot and I had to go back into gconf-editor to turn panel animation back on and then off again to get it back.

My solution: I now just keep panel animation on with the delay set to 0. The panel remains visible after reboot if I do that. I don't know what changed to make it not work anymore, but it's a small thing.

---

