---
title: "Keyboard Shortcuts no longer working after upgrade to 9.04"
date: 2009-05-01
forum: General Help
---

### Post by Mil Doc Jr on 2009-05-01
After upgrading from 8.10 to 9.04 I gained functionality of my HP quicklaunch buttons but now my computer doesn't recognize a more useful feature: the keyboard shortcuts.  I found this out earlier when I pressed alt f2 and nothing happened, I tried a restart, nothing. Looked for anything I could find and found something about it in a previous dist-upgrade from Hardy to Intrepid something about a console-common not being installed tried that, nothing.  Any ideas on how to troubleshoot this?

---

### Post by 6tangos on 2009-05-12
Hi, I'm having a similar problem.

It seems that some keyboard shortcuts work (for example (Ctrl-Alt-l to lock screen), however, others such as Alt+f2 (mentioned previously by Mil Doc Jr) don't work.
I'm reluctant to file a bug report just yet, until I've investigated a bit further. 

Anyone else experiencing problems? 

Mil Doc Jr, you mentioned that you'd seen a report of a similar problem with a past upgrade, can you post a link so I can have a look?

Thanks.

---

### Post by oneafrikan on 2009-05-19
I'm finding the following doesn't work:

1. alt-tab to switch btw apps
2. workspace switching doesn't work - ctrl-alt cursor keys
3. i have to set "visual effects" to "normal" every time I boot, to get windows working for everything....

Other than that, seems ok (although may have more problems once these are sorted!).

i've been looking at fglrx issues and i'm not sure this is related...

any ideas anyone?

---

### Post by compabeto on 2009-05-19
Others have experienced similar issues:

[http://ubuntuforums.org/showthread.php?t=1155027&highlight=keyboard+shortcuts]("http://ubuntuforums.org/showthread.php?t=1155027&highlight=keyboard+shortcuts")

[http://ubuntuforums.org/showthread.php?t=1160782&highlight=keyboard+shortcuts]("http://ubuntuforums.org/showthread.php?t=1160782&highlight=keyboard+shortcuts")

The last one says that it may be due to the commands plugin in compizconfig settings manager taking over the system > preferences > keyboard shortcuts. I've tried it myself and my shortcuts work now, it's just that you have to manually set them up.

---

### Post by oneafrikan on 2009-05-21
my solutions here:

[http://www.oneafrikan.com/archives/2009/05/19/jaunty-jackalope-upgrade-issues-evolution-window-decoration-workspace-switcher-alt-tab-not-working/](http://www.oneafrikan.com/archives/2009/05/19/jaunty-jackalope-upgrade-issues-evolution-window-decoration-workspace-switcher-alt-tab-not-working/)

---

### Post by xtracool_protik on 2009-05-24
Hi everyone,
 It seems there is some issue with 9.04 and keyboard shortcuts.
 First thing Jaunty doesn't allow me to use metacity over compiz but thats ok they improved a lot.
 Second thing I've working alt-tab. Super-space etc However more important things as alt-f2 and alt-f1 are missing it just doesn't make anything happen.
 If anyone can find a solution please post as soon as possible using mouse is pain :(

---

### Post by compabeto on 2009-05-30
If you have CompizConfig Settings Manager, try enabling the Gnome Compatibility plug-in, it provides support for Alt-F1 and Alt-F2, among others, and works great.

---

### Post by oneafrikan on 2009-06-02
@compabeto - done that and works fine - thanks.

---

