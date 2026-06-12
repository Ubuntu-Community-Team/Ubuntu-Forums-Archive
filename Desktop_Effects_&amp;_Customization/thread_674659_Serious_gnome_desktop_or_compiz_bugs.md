---
title: "Serious gnome desktop or compiz bugs"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by anthropop on 2008-01-21
I am running Gutsy and enabled the System->Appearances->VisualEffects->Extra selection.  Now I have serious window display crashes (like my post [http://ubuntuforums.org/showthread.php?t=674533](http://ubuntuforums.org/showthread.php?t=674533)).  I have found that reverting to a simple desktop does not solve the problem, now that the window mechanism is broken.  It is only certain windows in various applications that are broken, but my .xsession-errors file is overflowing with errors.  If I run an application with strace I get the kind of output listed in the 674533 post I mentioned.

I am certain it is confined to my /home account as others on my system do not have this problem.  If I export X windows by doing an ssh -X username@server from another machine I do not get the failure.  This means that all the files used by a particular application are intact, but the X window mechanism is broken for local display.

I had a couple of Gnome crashes after enabling the VisualEffects and then the problem started, but I can not correlate the exact sequence of events.  For example, one time I was dragging a window to a second desktop and the screen froze blank white.  I forced a reboot from an ssh session and came back up.  I do not know if this type of crash then injured a local file that is related to this bug.

I certainly wish I had not started playing with compiz!  Please help me restore my local display files so the applications stop crashing.  I would even like to continue to use compiz if there is some explanation for this behavior.  Right now I can't even send an email.

---

### Post by anthropop on 2008-01-21
I discovered that it was the Crux theme that is broken.  All that pain and work just to figure that there are serious bugs in individual themes.  Please let me know where to post the bug for a theme!

---

