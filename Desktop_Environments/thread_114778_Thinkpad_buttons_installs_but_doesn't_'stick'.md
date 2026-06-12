---
title: "Thinkpad buttons installs but doesn't 'stick'"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Robor on 2006-01-09
I've got an IBM T-42 with Ubuntu Breezy 5.10 installed.  I used Synaptic to install the Thinkpad buttons program (it's 'tpb' in Synaptic) and it works fine until I reboot.  After I reboot they buttons still work but there's no on-screen display feedback.  I can go to Synaptic and mark 'tpb' for reinstallation and they work fine again until the next reboot.  I've tried a removal and reinstall and a complete removal and reinstall but that didn't help.

---

### Post by vruum on 2006-01-09
just trying to figure out where the problem lies. What happens if you, instead of reinstalling the program, run it from a terminal? two ways to do that, 
1:open up a terminal and type:
> tpb
if that doesn't give you on-screen-display try:
> sudo /etc/init.d/tpb restart
if any of these give you on-screen-display, then it's just a matter of the program not starting properly, and easily fixable, if none of them work, then I guess it's google time

*edit* maybe I should take my own advice, it turns out someone smarter than me already did all the work. Here's a nice how-to:
[http://ubuntuforums.org/showthread.php?t=81622&highlight=tpb]("http://ubuntuforums.org/showthread.php?t=81622&highlight=tpb")

---

### Post by Robor on 2006-01-09
That worked like a charm...  Thanks!   :)

---

