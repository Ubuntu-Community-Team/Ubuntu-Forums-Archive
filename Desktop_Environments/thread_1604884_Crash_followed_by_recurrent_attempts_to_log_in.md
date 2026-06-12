---
title: "Crash followed by recurrent attempts to log in"
date: 2010-10-24
forum: Desktop Environments
---

### Post by Johees on 2010-10-24
hello all

For the last month or so, upon returning home, I find that my comp has crashed, with a blank screen (one lonely "_" in the top left, some other text that disappears before I can read it), followed by blank screen & the drum-roll for login in, then blank screen again. This happens recurrently.

Tonight however, it has happened after leaving the computer unattended for about 40mins, while listening to music. I have all power-saving features disabled.

Syslog shows many copies of the following: 

> Oct 24 21:13:53 jan-desktop gdm-session-worker[2712]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 24 21:13:54 jan-desktop kernel: [ 6222.555503] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Oct 24 21:13:54 jan-desktop kernel: [ 6222.555511] render error detected, EIR: 0x00000000
Oct 24 21:13:54 jan-desktop kernel: [ 6222.555540] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1160621 at 1160473)
Oct 24 21:13:55 jan-desktop kernel: [ 6223.303187] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Oct 24 21:13:55 jan-desktop kernel: [ 6223.303194] render error detected, EIR: 0x00000000

I checked, and /etc/gdm/custom.conf does not exist. No .conf files at all.

I apologise if this is a really looong post, but I'm really not sure where to even start to look for the problem: ie noob!

So, synopsis: possible problem with Gnome Desktop Manager causing a crash.

PS; is there a handy command for restarting the desktop?, because I keep on restarting everytime this happens.

Many thanks

---

### Post by Johees on 2010-10-25
OK, just disabled GL screensaver (to blank screen screensaver) for what its worth.
Also ran gdmsetup, but don't think the problem lies there.

I'm not sure what prompts the system to look for the non-existant /etc/gdm/custom.conf, but the only thing that precedes the > Oct 25 20:38:46 jan-desktop kernel: [18384.170429] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung, is an entry ~20 minutes before that one.

Will see if the screensaver thing does anything, will keep you peoples posted...:confused:

---

### Post by Johees on 2010-10-29
Disabling the GL screensaver seems to do the trick.

Had no crashes for the last 3 days.
Any further actions I can take, ie log this as a bug and do a proper compilation for a report?

Oh and info on my graphics controller:
> VGA compatible controller
/0/100/2


product: Core Processor Integrated Graphics Controller [8086:42]
vendor: Intel Corporation [8086]
bus info: pci@0000:00:02.0
version: 12
width: 64 bits
clock: 33MHz

Anything else I need to add?

---

