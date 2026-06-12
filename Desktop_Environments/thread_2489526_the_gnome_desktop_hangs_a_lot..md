---
title: "the gnome desktop hangs a lot."
date: 2023-08-01
forum: Desktop Environments
---

### Post by tojonukokhadush on 2023-08-01
i recently had the video display cable changed from the repair shop of my ols laptop running ubuntu 22.04; what i realize is the gnome desktop hangs a lot after that. although the system in total is old, it didnt use to hang the way it does now; the pointer freezes and doesnt move at all. but interestingly when i open any app for example the browser or file manager, then the touchpad is relatively smoother. the gnome is showing a lot of cpu usage as well. how to solve the issue, is it driver or any other issue? why only in desktop it happens?

---

### Post by DuckHook on 2023-08-02
Since this problem started right after you had your laptop repaired, it strongly suggests a HW issue. Perhaps the technician accidentally loosened the touchpad connection while replacing the cable (I assume it was an internal cable). You say the system hangs, but your detailed description mentions only a frozen touchpad pointer. Is the system totally hung, or is it just the touchpad?

Either way, you will need to play detective to get to the cause. This involves a process of elimination that can only be summarize in broad strokes.

[list=1]
[*]Back up all of your important data. This should be done as a matter of course, but is especially important when you are experiencing problems.
[*]Look at your logs (always the first step in diagnosing a problem). Learn how to use grep to filter for more manageable results. The most important log entries are those that occur right before and after a "hang".
[*]Try running a LiveUSB and note if the same problem is present.
[*]Plug in a mouse to see if it has the same problem.
[/list]
Aside from this very general advice, there's not a lot that any of us can do at a distance. You can try posting relevant log entries to this forum, but do not post entire logs—few forum members have the time or inclination to parse through whole logs—only the relevant parts.

You can also try taking your laptop back to the repair shop and asking them for further diagnosis, but in my experience, most repair shops know nothing about Linux and may do more harm than good monkeying with the OS.

---

### Post by tojonukokhadush on 2023-08-16
thank you. i appreciate the suggestion.

---

