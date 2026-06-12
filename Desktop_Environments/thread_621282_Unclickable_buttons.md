---
title: "Unclickable buttons?"
date: 2007-11-23
forum: Desktop Environments
---

### Post by newkirk on 2007-11-23
I just keep getting more and more irritated with this one. :(

To reproduce the bug try the following:

Fire up Synaptic.  While it's reading packages and figuring stuff out, all the buttons across the top are ghosted out.  WHILE this is the case, position the mouse cursor over one, like the 'search' button.  Once Synaptic is finished preliminary work, it displays packages and the buttons are now unghosted and clickable.  So try clicking on the one you're already hovering the mouse over...  It won't work!  Not until you have moved the mouse cursor completely outside the button bounds and back over it again, or switched windows and back, workspaces and back, etc.

It seems apparent to me that when the buttons are unghosted, it needs to re-check for 'mouseover' event or what-have-you, but does NOT.

It's not just Synaptic, it's global - every button I've seen in any app that can transition between states like this (unclickable to clickable) has done the same thing if I've tried.  Synaptic was just a handy example, and the place where I most often encounter it in daily usage.  (I'm endlessly starting up synaptic and staring at it stupidly for 10-15 seconds while it figures **** out, waiting for the buttons to unghost so I can move the mouse and click on 'search')

Is this just me?  I've searched the forums for any conceivable set of keywords that should show up in a description of this problem, and come up empty-handed.

j

---

### Post by newkirk on 2007-11-27
Nobody?  Am I the only one who experiences this bug, or does it just not bother anyone else?

j

---

### Post by newkirk on 2007-12-05
Wanted to post this in case anyone finds this thread in a search for this bug.

I reported it as a bug at Xfce, and was referred to an ongoing (6.5 years since first report!!) bug in GTK ([http://bugzilla.gnome.org/show_bug.cgi?id=56070](http://bugzilla.gnome.org/show_bug.cgi?id=56070)).  Seems the GTK folks may actually be getting close to having this resolved in a release.

j

---

