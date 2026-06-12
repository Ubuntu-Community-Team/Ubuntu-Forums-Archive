---
title: "Rhythmbox: Play key works universally, forward/back don't"
date: 2010-10-29
forum: Desktop Environments
---

### Post by TrevorBradley on 2010-10-29
Quick question.  I'm running Ubuntu 10.10, and I notice that the "Play/Pause" key on my keyboard works to start and stop Rhythmbox from any open app.  However, my keyboards "Back" and "Forward" keys only work when the Rhythmbox app is active.

Now I know that some apps like Firefox use Back and Forward for navigation.  Is there anywhere I can reconfigure this behaviour?

Thanks in advance!

---

### Post by vexorian on 2010-10-29
First we need to know if it is a problem with the keyboard support in general or just rhythmbox.

Open some media file with totem (movie player) and check if the keys work.

---

### Post by TrevorBradley on 2010-10-29
The back/forward keys work fine in Firefox to navigate back and forward.

The keys even work great in Rhythmbox to skip to the next/previous song, the exact behaviour I'm looking for.

What I'm wondering is why the play/pause button works universally (say, while running firefox) while the back/forward keys appear to be bound to a specific application, and is it possible to change that.

---

### Post by vexorian on 2010-10-29
Ah ok, I see. Sorry. In my case, my keyboard has different keys for media Next and Previous and browser back and forward.

How about trying system\preferences\keyboard shortcuts? It control's gnome's global shortcuts, so you can try and verify if the Next and Previous song have the shortcuts correctly assigned.

---

### Post by TrevorBradley on 2010-10-29
Oh awesome, that works!

XF86AudioBack -> XF86Back
XF86AudioForward -> XF86Forward

..does the trick.  I don't really use these keys for browsing, so it's perfect.

I didn't realise that the keyboard was so configurable... I've now also configured hotkeys to switch to workspace #N, or move the current window to workspace #N.  Productivity!

Thanks so much!

---

