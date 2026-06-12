---
title: "Kontact/Kalendar &quot;locked&quot; by unknown application"
date: 2006-01-30
forum: Desktop Environments
---

### Post by thesnowysoviet on 2006-01-30
Kontact has previously worked just fine.  Without my changing any settings, it still starts up fine... but I can't maipulate it.  No new todo's or events, no modifying existing ones, nothing.  I can still sync with my Palm m125 via kpilot; the palm works fine and events sync properly to Kontact, but all Kontact seems to be capable of doing is displaying things.  No good.

Double-clicking on an event or todo gives this pop-up message: "Unable to edit incidence: it is locked by another process."  There's nothing in my process tree I can see that would be "locking" Kontact, and in case it was kpilot (which, mind you, has worked before!), I killed kpilot and tried again.  Nothing changed.

What is going on?

---

### Post by Sokraates on 2006-01-30
[quote=thesnowysoviet]Kontact has previously worked just fine.  Without my changing any settings, it still starts up fine... but I can't maipulate it.  No new todo's or events, no modifying existing ones, nothing.  I can still sync with my Palm m125 via kpilot; the palm works fine and events sync properly to Kontact, but all Kontact seems to be capable of doing is displaying things.  No good.

Double-clicking on an event or todo gives this pop-up message: "Unable to edit incidence: it is locked by another process."  There's nothing in my process tree I can see that would be "locking" Kontact, and in case it was kpilot (which, mind you, has worked before!), I killed kpilot and tried again.  Nothing changed.

What is going on?[/quote]

I've had this problem with Firefox 1.5 once. KDE gave me the same error message, even though no process was blocking it (or at least none I could see). Logging out and back in solve it for me.

Till now I don't know waht caused the mess.

---

### Post by thesnowysoviet on 2006-01-30
Logging out/ back in doesn't help... neither does rebooting.  I think my best option would be to risk exporting the calendar data, uninstalling kontact, reinstalling, and importing the data.

---

### Post by GeneralZod on 2006-01-30
[QUOTE=thesnowysoviet]Logging out/ back in doesn't help... neither does rebooting.  I think my best option would be to risk exporting the calendar data, uninstalling kontact, reinstalling, and importing the data.[/QUOTE]

First, try 

```

find ~/.kde -name "*lock*"

```

when you are *not* logged in to KDE (log out of KDE, hit CTRL+F1) and see what files are reported.

---

### Post by cyklotronen on 2006-02-03
I hade the same problem and solved it by deleting all files in the 
~/.kde/share/apps/kabc/lock/
directory.

---

### Post by thesnowysoviet on 2006-02-04
[QUOTE=cyklotronen]I hade the same problem and solved it by deleting all files in the 
~/.kde/share/apps/kabc/lock/
directory.[/QUOTE]

There's no directory named "kabc" in "~/.kde/share/apps".

---

### Post by GeneralZod on 2006-02-05
[QUOTE=thesnowysoviet]There's no directory named "kabc" in "~/.kde/share/apps".[/QUOTE]

Did you try my suggestion? If so, please post the output here.

---

### Post by thesnowysoviet on 2006-02-16
[QUOTE=GeneralZod]Did you try my suggestion? If so, please post the output here.[/QUOTE]

Sorry it took so long to get back to you... college has this whole "work" thing associated with it, apparently.  Go figure.

Anyway, "kabc" appeared after an uninstall/reinstall of Kontact under ~/.kde/share/apps.  As per your suggestion, here's the output:

~/.kde/share/config/clock_panelapplet_kubuntu_rc
~/.kde/share/apps/kabc/lock
~/.kde/share/apps/kabc/lock/_home_andy_.kde_share_apps_korganizer.std.ics.lock

A-ha?  Should that last one be dealt with?

---

### Post by thesnowysoviet on 2006-02-16
[QUOTE=GeneralZod]Did you try my suggestion? If so, please post the output here.[/QUOTE]

Problem solved!  I took the suggestion of Cyklotronen and deleted all files in ~/.kde/share/apps/kabc/lock, and Korganizer now works just fine.  Thanks to all for your input and help!

---

