---
title: "Make Old Box File Server, Using *APM*, Getting Gnome/HAL to Use It, Too"
date: 2009-01-22
forum: General Help
---

### Post by OverclockedMind on 2009-01-22
OK, that was probably too big a title, sorry if it is.

I have this old box that I would like to use Ubuntu on, to turn it into a file server. Actually, it was a file server at one point, but isn't any longer, as I couldn't get it to suspend-to-RAM. I accomplished this using the server install of 8.04; pushing the power button would shut it down cleanly, or bring it back up again as needed.

What I would *like* to see it doing, though is sleeping/suspending/et cetera to conserve power, instead of manually having to flip it off and on.

ACPI and this ancient machine, (PII 450, Gateway G6-350) well they dont seem to get along. I decided to try using APM, by putting "apm=on acpi=off" in the right spot in /boot/grub/menu.lst.

After some more Googling, I found that if running APM, that "apm -s" should cause the machine to suspend-to-RAM (which is ultimately what I want, not just the lighter sleep state.)

Entered that as root, and the machine suspended. (Rather oddly, though, as it suspended, the hard drive re-awoke, and then spun down again.) Except, when it was awakened, I was greeted with this:

```
ata:1.00 revalidation failed (errno=-5)
```

I have also seen this in the logs:

```
ata1:00 failed to IDENTIFY (I/O error, err_mask=0x4)
```

It didn't lock solid, freeze, or anything show-stopping though.
I forced a fsck next reboot, which went just fine.

OK, with that as background, here are my questions.


1) Is it still likely that I'm corrupting filesystems? This is just a test box right now, so if so, no big, but that'd never fly in a server role, obviously.

2) Is it possible to get gnome-power-manager (which from what I hear relies on HAL) using APM and not ACPI?

3) Since I have "switched" to APM, is there some way to force Gnome to regenerate its list of whats possible (sleep, hibernation, et cetera) so that I might get more options in Power Manager and the Shut Down dialogs?

4) If this means it's trashing filesystems, is impossible to get going automagically, and is just a no-go in general, how does one pick a used box out of a bunch (flea market, swap meet, what have you) that is likely to be fully ACPI compliant, supporting hard disk spindown, sleep, and waking without freaking out?

5) (I dont wanna do this but it's worth asking) Assuming I wanted to build a new, cheap-as-can-be box to use for this role, how can I verify its compatibility with sleep, as well as hardware compatibility (I'm thinking NICs, integrated video, et cetera here.)


Just having fun, and hoping maybe I can make this hardware do what I want it to do. Any answers would be greatly appreciated.

Best regards,
Joshua

---

