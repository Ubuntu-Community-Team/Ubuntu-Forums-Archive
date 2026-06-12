---
title: "Emacs interacts badly with Alt-F1 and clicking on system menus"
date: 2009-05-29
forum: General Help
---

### Post by DrHow on 2009-05-29
I suspect that what I am reporting is a bug; but perhaps someone has a suggestion for how to work around it:

The problem exists with absolutely plain Emacs: emacs -Q

If the Emacs window has the focus, then an attempt to bring up one of the system menus (Applications, Places, or System) either by mouse click or by Alt-F1 causes the system to go into a wrong state for 5 to 10 seconds.  During this time, no input events from either the keyboard or mouse are detected.  If one attempts no such additional input during the wrong state, then eventually the menu will pop up and things start working again.  If one does try additional input, such input may supercede the original menu request that put things in the wrong state.  E.g., if I click on "Applications" and then on my Firefox launcher in the panel, then Firefox starts launching after about 5 or 10 seconds and the Applications menu does not appear.

Clicking on other launchers and whatnot on my panel does not cause the problem.  I have never seen the problem when any application besides Emacs has focus.  The symptoms do not point squarely at either GNOME or Emacs, but both must be contributing somehow.

At this point my only workaround is to remove focus from Emacs before trying to get one of those menus.  (or swear because I forgot :( )

I am running Ubuntu 9.04.  

Emacs version:
GNU Emacs 22.2.1 (i486-pc-linux-gnu, GTK+ Version 2.14.1) of 2008-09-05 on vernadsky, modified by Ubuntu

Being a curious sort of person, I would be interested in speculation on what could cause such  a strange symptom.  Better yet - a fix!

---

### Post by jpkotta on 2009-05-30
Does the problem appear with emacs-snapshot (emacs23)?

---

### Post by DrHow on 2009-05-30
> **jpkotta said:**
> Does the problem appear with emacs-snapshot (emacs23)?

No.  I did not even know about the availability of Emacs 23; and I am very happy about it because the fonts actually look good!  And there is now real choice for fonts.  Having come from Windows, the lack of font smoothing with version 22 was something I was regarding as a step backwards.  This huge improvement on the font front is far more significant to me than absence of the apparent bug I reported.  If I don't have much trouble with the new version, I will stick with it - even if it currently lacks the Canonical 'seal of approval'.  Thanks for calling my attention to the existence of emacs-snapshot.

---

