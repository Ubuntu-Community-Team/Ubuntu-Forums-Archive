---
title: "Missing WINE app in Gnome Panel"
date: 2008-04-23
forum: Desktop Environments
---

### Post by frogotronic on 2008-04-23
Hello,

  I've done a clean install of Gutsy Gibbon and everything works very well, except for a strange error/bug with just one program.  The problem is that when I start the program, I do not see a bar in the bottom Gnome Panel.  So when the program is minimised, it "disappears".  It is actually still running, but impossible to bring back, or maximise (even with ALT-TAB).  The problem only occurs when using a WINE installed application (called BioEdit).  On my last iteration of Gutsy it installed and worked as expected.

  I've uninstalled/reinstalled the BioEdit application.  Also removed Wine, reinstalled WINE.  No change.  All other WINE apps behave as per normal, as an example I have WINE notepad and the misbehaving app opened at the same time - see screenshot for illustration of the problem.

  I think the issue is an app specific parameter setting to tell WINE to create a panel in GNOME.  Any idea how I would do this (short or a compete reinstall of the O/S)?

Thanks,
CH

---

### Post by frogotronic on 2008-04-25
1) Uninstall wine 0.59
2) Delete .wine
3) Install wine 0.50
4) reinstall wine apps


Conclusion: wine 0.59 is a regression of a much earlier bug.

:guitar:

---

