---
title: "User suddenly stops booting - looks like Marco"
date: 2017-04-09
forum: Desktop Environments
---

### Post by webmiester on 2017-04-09
Hi Everyone,

I was setting up a user account and I got it pretty much perfect already.  Then I started noticing that the top panel of my windows were missing (the ones with the minimize and maximize buttons and the name of the window).  So I went to the mate tweak tool and changed the windows manager to "Marco (no compositor)".  The top panels came back.  when I shift it back to "Marco (software compositor), the top panel disappears.

After reloading, the user's said account wont open properly.  It just loads the default background, then stops.

I pressed cntr-alt-F1 and got a text login screen.
I used the command "marco --display=:0 --replace"
I get the error:
Invalid MIT-MAGIC-COOKIE-1 KeyWindow manager error: Unable to open x display

When I try "mate-panel --reset", I get the error: "(mate-panel:2554) Gtk-WARNING **: cannot open display:"

at this point, I cannot get back to my GUI and have to shutdown the system.

This is a raspberry pi 3 running on ubuntu 16.04 mate by the way.  only one user account is affected, but its the one linked to the guess user account so the guess user account behaves in the same way.

What do you guys think went wrong, and how do I return it to the way it was before?

Thanks so much

---

