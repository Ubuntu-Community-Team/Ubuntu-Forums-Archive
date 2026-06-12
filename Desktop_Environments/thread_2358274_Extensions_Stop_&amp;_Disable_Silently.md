---
title: "Extensions Stop &amp; Disable Silently"
date: 2017-04-11
forum: Desktop Environments
---

### Post by Chris_Chambers on 2017-04-11
Currently running the 17.04 beta 2 release, but this issue followed me from 16.10.

I have a modest collection of extensions enabled.
[LIST]
[*]Dash to dock
[*]No topleft hot corner
[*]Topicons plus
[*]User themes
[/LIST]

My problem is that all the extensions take turn silently stopping and disabling. I'll look for the tray icons and find they're back in the BL corner with no error notification or bug report dialogue. The next time I may find that I move the mouse into the TL corner and unexpectedly open Activities. 

Each time I go into the tweak tool, I find that one of these four extensions is turned off. I turn it on and continue. I've not been able to discern a pattern or correlation with any particular task and indeed every extensions takes a turn at being the victim. 

I've looked but haven't found a reported bug that matches this behaviour. I'm ok to dig a little and try to find the problem, but I'm unsure of where to look. Right now I'm running [FONT=courier new]journalctl[/FONT][FONT=courier new] /[/FONT][FONT=courier new]usr[/FONT][FONT=courier new]/bin/gnome-shell -f -o cat[/FONT] while I work to see if anything interesting comes up. Of course, when I'm watching - it doesn't happen.

Any suggestions for troubleshooting steps are welcome in lieu of a "when I had that problem I did this and fixed it."

Cheers!

---

