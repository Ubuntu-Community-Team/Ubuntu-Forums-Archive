---
title: "&quot;Child&quot; windows get lost and/or moved by Unity"
date: 2012-07-05
forum: Desktop Environments
---

### Post by ubnewbie2 on 2012-07-05
I have managed to lose 'child' windows in Unity a few times.  

For example, I started composing a new message in Thunderbird (so Thunderbird pops up the child window for composing the new message), and wanted to verify something in Wikipedia, so I clicked on the browser in the launcher (which was running in a different workspace) and it switched to that app/workspace.  I completed my search, then clicked on Thunderbird's icon in the launcher to switch back.  But nothing happened.

I manually went back to the workspace containing Thunderbird, but the 'compose message' window was gone.  I found it, all by itself, in a 3rd workspace using the workspace switcher !!

---

### Post by msammels on 2012-07-05
That sounds like a bug. 

> Ever since the first computers, there have always been ghosts in the machine. Random segments of code that have grouped together to form unexpected protocols. Unanticipated, these free radicals engender questions of free will, creativity, and even the nature of what we might call the soul. Why is it that when some robots are left in darkness, they will seek out the light? Why is it that when robots are stored in an empty space, they will group together, rather than stand alone? How do we explain this behavior? Random segments of code? Or is it something more? When does a perceptual schematic become consciousness? When does a difference engine become the search for truth? When does a personality simulation become the bitter mote... of a soul?

No, but seriously. You say the windows move randomly between workstations? Does this only happen with Thunderbird, or does it happen with other applications?

---

### Post by ubnewbie2 on 2012-07-05
> **msammels said:**
> That sounds like a bug. 



No, but seriously. You say the windows move randomly between workstations? Does this only happen with Thunderbird, or does it happen with other applications?

Well, when using the launcher to switch between apps/workspaces, yes.  Not the original Window, just the 'child'.  I'll try to find another app like Thunderbird that launches a child window and test it.

Another app it struggles completely with is a java app I use, called JP passwords.  When it has a child window open, sometimes even when not, I often can't find it again anywhere.  One time it was half off the edge of a workspace!

A bug?  Yep, I think so :)

---

### Post by ubnewbie2 on 2012-07-06
OK, verified.   I opened the home folder in Nautilus, right clicked on a text file and opened it in gedit.

I then used Launcher to switch back to Chromium (in a different workspace), then to switch back to Nautilus.  The result was a bit different this time - Nautilus popped up, in the same workspace as Chromium (where it wasn't before), and half off the screen to the left.

The desktop is definitely forgetting/changing window positions.

---

