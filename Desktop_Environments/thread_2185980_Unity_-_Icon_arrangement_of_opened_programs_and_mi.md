---
title: "Unity - Icon arrangement of opened programs and minimizing windows"
date: 2013-11-05
forum: Desktop Environments
---

### Post by ag4032 on 2013-11-05
Hello,  is there a way, either by installing additional software or modifying unity settings, to minimize windows by pressing the corresponding program icon in the unity bar? Second question, is there a similar possibility to make icons of opened programs automatically move on the top of the bar (below the other currently opened ones) until the are closed again (and return to the previous position)?  Thanks.

---

### Post by christopher-lees on 2013-11-05
> **ag4032 said:**
> Hello,  is there a way, either by installing additional software or modifying unity settings, to minimize windows by pressing the corresponding program icon in the unity bar?
 
No there's not, and I doubt there ever will be. It would fundamentally break Unity's window management facility, as in, if there were visible windows and minimised windows, you'd never be able to get back to any minimised windows except for the last one used!

The whole "Click to show and click again to minimise" is pretty bad interface design - very confusing for users unless they are aware if the window is visible or hidden. I'm glad Unity doesn't implement it "because Windows users are used to it".

> Second question, is there a similar possibility to make icons of opened programs automatically move on the top of the bar (below the other currently opened ones) until the are closed again (and return to the previous position)?  Thanks.

Not a bad idea as an option, but sadly no it's not possible in Unity. I do find that I prefer it the way it currently is, because my icons are always in the same place whether their programs are open or closed. In other words, muscle memory.

---

### Post by ag4032 on 2013-11-05
> **christopher-lees said:**
> It would fundamentally break Unity's window management facility, as in, if there were visible windows and minimised windows, you'd never be able to get back to any minimised windows except for the last one used! What do you mean by saying it wouldn't be possible to go back to any of the minimized windows? Any of the opened programs would be shown again by clicking on it's icon.

---

### Post by 3rdalbum on 2013-11-06
> **ag4032 said:**
> What do you mean by saying it wouldn't be possible to go back to any of the minimized windows? Any of the opened programs would be shown again by clicking on it's icon.

That would work fine for one window. What if you had three windows of the same program open, and one window was minimized?

I think what christopher was trying to say is that "click to minimize" doesn't make sense when what you are clicking is a whole application, not just a window. You couldn't implement this option in Unity.

If you are absolutely wedded to this and can't possibly use any operating system that doesn't let you click-to-minimize, you could try a different desktop environment like KDE, or XFCE, MATE or Cinnamon. You can install any or all of these onto your current Ubuntu and then choose the desktop at the login screen.

---

### Post by mc4man on 2013-11-06
This was partially implemented in an early version on unity & and while it worked fine was removed along with left click to spread pulling windows from _all _workspaces
(there was a progression of what l. clicks on the icon would produce, orig [progression here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733/comments/4")

As far as straight minimizing on the focused window that [was always rejected]("https://bugs.launchpad.net/ayatana-design/+bug/733349") though 1 means to do so [was proposed]("https://bugs.launchpad.net/ayatana-design/+bug/733349/comments/58") & again rejected
For a while it was implemented thru ppa builds but at this point there is no practical way to use that patch so what you see now is what you get.

Other docks like docky & plank still do this to some extent though I don't believe they can do 'spread' thru the l. click

---

