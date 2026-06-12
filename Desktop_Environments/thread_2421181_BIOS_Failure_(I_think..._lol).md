---
title: "BIOS Failure (I think... lol)"
date: 2019-06-17
forum: Desktop Environments
---

### Post by gargarr on 2019-06-17
Hey there Smarter Than Me Ubuntu Crew :),

I seem to be experiencing a very confusing issue that I am having a hard time finding a solution for. Once my computer is turned off for a little while (couple hours to half day, so memory seems to be wiped), upon turning on the computer the first boot fails.

The meaning of failure is that the visual is not coming through. Instead, I am giving a black/blank screen. There is no BIOS option to the motherboard just a blank screen. Pressing keys, moving the mouse, and any other I/O interaction has no effect on the response. Also, waiting doesn't do anything... I tried to be patient (lol).

Solution working atm: Hitting the power button to the battery and then flicking it back on seems to clear this issue first try and I am brought to the de-encrypt landing page, I enter the password, then I am brought to the Ubuntu landing page for the user account, and then in.

After that, things are smooth sailing.

The issue only occurs at the time of first boot after a set of hours have passed. Also, this tower was in use of Windows 10 before this Ubuntu refresh, and Ubuntu is the only OS on this HD. Too, the encrypt was set up at the time of install and only for the current data on the system and not the entire HD.

What do you guys think? If there are some terminal commands, I would love to get some help to do some diagnostic digging... I am just not sure what those commands or where I should start looking.

Thanks for your help :)

---

### Post by CatKiller on 2019-06-18
It sounds to me most like the watch battery on the motherboard being flat. I mean, it could be something more complicated, but a new one is pennies, so it's where I'd look first.

---

### Post by garvinrick4 on 2019-06-19
Look to oldfred for all problems of boot when in difficult situation               

                                                [URL="https://ubuntuforums.org/member.php?u=852711"]oldfred


[/URL]

---

### Post by oldfred on 2019-06-19
+1 on CatKiller's suggestion as first thing to try.

Note that UEFI/BIOS settings reset system to defaults.  And loss of battery power may reset UEFI/BIOS settings also.

So any settings you changed in UEFI/BIOS need to be redone. My motherboard has multiple settings I change, some required & some optional. With old BIOS system I had to redo all and kept a list. Newer UEFI saves some settings, so I do not have to redo all & it lets me do screenshots, so I know setting & which tab to use to change settings.

If that is not it, then is UEFI/BIOS most current version available for your system?

---

