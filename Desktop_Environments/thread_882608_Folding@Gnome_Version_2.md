---
title: "Folding@Gnome Version 2"
date: 2008-08-07
forum: Desktop Environments
---

### Post by ruudiculus on 2008-08-07
It's been a while (a full year I believe :oops:) but I'm finally working on F@G-V1.20's follow-up (F@G-V2)! At this point all main functionality is present and I thought it might be a good idea to made the current build available as an Appetizer.

**What's new**
[LIST]
[*]System tray icon works in both Gnome and KDE
[*]Monitoring of multiple F@H processes now possible
[*]Also works with latest F@H-V6.02
[/LIST]

**What doesn't work yet**
[LIST]
[*]Editing settings per F@H-client
[*]Not tested yet on x86_64
[*]Autostarting individual F@H-processes on applet-launch
[/LIST]

**Where to download**
[_HERE_]("http://www.ruudbeukema.nl/engineering/fag/fag2-appetizer.tar.gz")

**What to do with feedback/suggestions etc.?**
Give it to me! Please use my [_contact form_]("http://www.ruudbeukema.nl/contact.php")

Enjoy!

---

### Post by ruudiculus on 2008-09-20
**Finally!!!!**

Folding@Gnome 2.0 is a fact! You can download it on my website: [www.ruudbeukema.nl]("http://www.ruudbeukema.nl/linux/fag.php")

**Main features**
[LIST=1]
[*]Monitoring multiple Folding@Home clients
[*]Works with Gnome and KDE
[*]Views the protein folding in 3D(!)
[*]Visiting statistics page online
[*]Precompiled for Debian Etch (x86)
[*]Easy compilation for other targets
[/LIST]

There are several ways to auto-start a Folding@Home client and there's a link on my page to a clear howto on how to do that.

---

### Post by ruudiculus on 2008-10-30
I got reports of people failing to compile fag-2.0.2 because of the fact that './configure' is looking for gtkmm-2.0 libraries etc.

Ubuntu users use the gtkmm-2.4 library, so I tried to compile F@G-2.0.2 against that library; with success!

You can download precompiled F@G-2.0.2 for gtkmm-2.4 as well as its source made ready for gtkmm-2.4) from my website: [www.ruudbeukema.nl]("http://www.ruudbeukema.nl")

Let me know if you experience any problems, since I don't have a gtkmm-2.4 system here to test it on (the gtkmm-2.4 f@g-executable defaults to using gtkmm-2.0).

---

