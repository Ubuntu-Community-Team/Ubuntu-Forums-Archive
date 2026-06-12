---
title: "When Compositing is enabled, screens are duplicated but not mouse"
date: 2011-07-28
forum: Desktop Environments
---

### Post by kloplop321 on 2011-07-28
So, here's my problem, I have 3 screens, two powered by a GTX 450, and another screen powered by another GTX 450.

When I have composting off, the three screens work just dandy, other than the lack of some eye candy. I tried to test it in a minimal environment: xfce.

Before I continue, here's what I've already done:
Gnome has the same problem. 
KDE refuses to enable compositing, it mysteriously complains about some other application preventing it.

Back to the situation at hand however:

When I enable compositing in both Gnome and xfce, the left-most screen is duplicated across all screens. The mouse however is not. I can take my mouse over all the screens(it will not show up anywhere else)
I can drag windows around, and see my cursor with the hand on my first screen with the window, I drag it to the second screen(and on my second screen, I see the window leave the screen, just like the first), and the mouse has the same cursor with the hand, still dragging, but no window on the second screen, I can drag back to the first screen, and see the window again.

If I try to disable compositing, Xorg crashes, and I must go to a TTY output(Ctrl+Alt+F#), and do sudo killall Xorg, and then Xorg resets.

Here's a video basically showing whats going on except the crashing on compositing disable.

[http://www.youtube.com/watch?v=jnZK3IzuAgM](http://www.youtube.com/watch?v=jnZK3IzuAgM)
Its 2 minutes long.

Thanks in advance

---

