---
title: "Dual/multi monitors workspace behavior is illogical [13.04]"
date: 2013-09-25
forum: Desktop Environments
---

### Post by djvictoid on 2013-09-25
I've searched high and low, and I can't find a working solution to the following multi-monitor scenario.

Actual behavior:

I have a laptop with an occasionally-attached second monitor.  When the second monitor is attached, the number of workspaces is doubled into workspace "pairs."  When switching the active workspace (control-alt-arrows), workspaces in both screens are switched simultaneously to an adjacent pair of workspaces.  When casting a window to an adjacent workspace (control-alt-shift-arrows), the window is not moved to an adjacent monitor, but it's moved to an adjacent (off-screen) workspace in a pair.  In this way, a window can't be moved to the adjacent monitor's workspace (since it is obligately tied to one side of the pair or the other).

Expected behavior:

Connecting an additional monitor does not change the number of workspace panels.  The two monitors simply show adjacent workspaces within the same set.  Shifting the workspace with control-alt-arrows moves within the same set of workspaces and can move a workspace between monitors.  Moving windows between workspaces with control-alt-shift-arrows can move windows between adjacent workspaces and, therefore, adjacent monitors.

There are numerous threads on this, but I can't seem to use the right search terms (or options in compiz) to find a working solution in 13.04.  Any suggestions are appreciated.

---

