---
title: "gnome 2 and multiple desktops (using classic interface without effects)"
date: 2011-05-03
forum: Desktop Environments
---

### Post by egandt on 2011-05-03
First off if you want multiple desktops then you must disable compiz (this needs to be documented somewhere), which is fine I have done so, and now I have 2 nice desktops.  

With 2 start menus and everything, but I have a problem:
On the second monitor (AKA desktop) I can not add any major items to the panel (such as Workspace switcher, Windows Selector, Trash, System Monitor ...), yet I can add others such as Shutdown or search for files to the bars, now as anyone will tell you without (Workspace switcher, Windows Selector) the second monitor is of little use.

The error is simple:
"Window Selector" has quit unexpectedly
If you reload a panel object, it will automatically be added back to the panel.

I did not have such a problem with gnome on Ubuntu 10.04LTS before I upgraded so I assume this is a new issue.  In fact I can see when I add these items to the panel on desktop 2, they pop-up on desktop 1's panel for a second before the error occurs.  Does anyone know how to fix this problem?


Update, based on this link: [https://bugzilla.redhat.com/show_bug.cgi?id=650638]("https://bugzilla.redhat.com/show_bug.cgi?id=650638")  The problem is gnome 2.32 it should work if gnome 2.30 is used instead.  Bummer that 2.32 is shipped with Ubuntu 11.04 then.  Question any way to move back to using 2.30 in 11.04?

ERIC

---

