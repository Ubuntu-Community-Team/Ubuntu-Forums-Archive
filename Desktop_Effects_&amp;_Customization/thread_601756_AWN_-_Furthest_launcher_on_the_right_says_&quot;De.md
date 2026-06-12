---
title: "AWN - Furthest launcher on the right says &quot;Desktop&quot; and doesn't launch anything"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by Erowid on 2007-11-03
Here's what I'm seeing:

[IMG]http://www.crapulent.net/userpics/awn-issue.png[/IMG]

I tried removing the "View Desktop" applet thing to see if that might have been affecting it, if I move the launchers around, whatever one's on the far right does the same thing...  Wondering if anyone else has bumped into this, and has maybe found a solution?

---

### Post by Erowid on 2007-11-04
Thought I'd give a quick update in case anyone else bumps into this issue:

I removed all launchers from AWN, then added again via gconf-editor.  I'm still seeing the Desktop in the preview when the app associated with the launcher isn't running, but, at least the launcher functions at this point.

---

### Post by Erowid on 2007-11-05
Err, problem unfixed... It seemed to work fine for a while (as per my last post), but no longer. Tried what I did last time, and no dice.

It's almost as if... When CompizConfig (launcher in question) is closed, it somehow associates it with the open application(?) "Desktop" ... I moved "Desktop" to another workspace, and now it launches CompizConfig no problem, but, umm... It also stopped drawing my desktop (can see right through to my skydome, and it doesn't re-draw the screen after you move something, actually kinda entertaining.... I'm sure it'll get fixed once I restart gdm though).

---

