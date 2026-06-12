---
title: "gutsy kde4 composite radeon"
date: 2008-01-15
forum: Desktop Effects &amp; Customization
---

### Post by thematrix on 2008-01-15
Hi all,

I'm having trouble getting the composite features in kwin up 'n running...
I have a Radeon Mobility 7500 in a thinkpad T40, which btw works great with aiglx/compiz fusion. But when I enable the desktop effects in kde4 I get no composite features...
This is what the log files try to say to me:

[I]kwin(8659) KWin::CompositingPrefs::detect: glx version is  1 . 2
kwin(8659) KWin::CompositingPrefs::detectDriverAndVersion: GL vendor is "Tungsten Graphics, Inc."
kwin(8659) KWin::CompositingPrefs::detectDriverAndVersion: GL renderer is "Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL"
kwin(8659) KWin::CompositingPrefs::detectDriverAndVersion: GL version is "1.3 Mesa 7.0.1"
kwin(8659) KWin::CompositingPrefs::detectDriverAndVersion: XGL: no
kwin(8659) KWin::CompositingPrefs::detectDriverAndVersion: Detected driver "unknown" , version ""
kwin(8659) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"
systemsettings(8899) KCMultiWidget::apply: "desktop"   "desktop"
QCoreApplication::postEvent: Unexpected null receiver[/I]

I'm new to kde4, but it looks like it doesn't see my radeon driver as supported:
Detected driver "unknown" , version ""

fglrx is not an option and setting it to ati gives the same result...

anyone got this working with a similar config???

I would like to try this out before using going back to compiz fusion...

Thanks,

Frederic

---

