---
title: "Fonts display issue under Ubuntu Gnome"
date: 2011-08-01
forum: Desktop Environments
---

### Post by johnitsa on 2011-08-01
Hey guys,

I'm facing a pretty annoying issue on my Ubuntu installation. Randomly, it just stops displaying certain characters properly (see attached printscreen). As far as I've looked into it, I can't find any reason for it (nor can I reproduce it on purpose).

Sometimes, it just affects text in web pages. Other times, it affects the whole system, including window bars, right-click menus, the terminal and text written in various editors. I can usually fix this by doing a reboot, but at some point it happens 2-3 times a day, and I can't spend this much time constantly rebooting.

My laptop is an Asus Eeepc 900, running Ubuntu 11.04 with Gnome 2.32.

Do you have any idea what might be the cause? I wasn't able up till now to find something relevant on the internet.

Thanks,
Andrei

---

### Post by wojox on 2011-08-01
> **johnitsa said:**
> 
My laptop is an Asus Eeepc 900

I thought I was the only one. :P

I don't know what it is but I've learned to live with it. Maybe I'll look around some now that it doesn't effect just me.

---

### Post by skimtneer on 2011-08-01
I have a problem of similar description but a different visual effect.  As long as I'm running Gnome+Metacity (Ubuntu/Gnome Classic desktop (No Effects)) -- Randomly, I get weird "wrinkles" in my text.  Mostly in web pages and other text windows, but at times it can affect window title bars and everything.  But mine looks different than yours.  My issue seems to be with subpixel font smoothing/hinting.  What I get looks like certain characters are shrunk or wrinkled so that they are a fraction of a pixel narrower.  Now on a word by word basis that's just hard to read but it wouldn't be a total disaster.  What makes it far worse is that when this is happening to an entire web page, the overall effect is that the entire window contents wiggle as the font rendering gets recalculated with each change in window content.  Every character I enter, in some cases, causes the whole window to wiggle or ripple by a sub-pixel amount.  This is more prominent in certain websites that use certain CSS techniques, I think; I see it MUCH more in Gmail and Facebook.  On Facebook every single character I enter into a textarea input box sometimes causes the window contents to ripple.

This is awful, it's making my digitally (DVI) connected LCD monitors act almost as bad as if they were analog connected or as if they were CRTs with poor pixel timing.

So why, you may ask, am I using Gnome Classic and Metacity?  Compiz doesn't have this problem,  Unfortunately, Compiz freaks out and corrupts the display when I move windows from monitor to monitor.

This is all related to the fact that my desktop spans 3 monitors side by side in portrait orientation to give a large working area without taking up too much space on the desk.  Neither Compiz nor Metacity show the problems mentioned above when I don't use portrait orientation.  But at this point I seem to be forced to choose between accepting display corruption or giving up my preferred desktop configuration.  I don't want to sell a monitor and go back to two in landscape mode.  So for now I'm suffering with the subpixel ripple problem in Metacity because the problem with Compiz is far worse.

---

