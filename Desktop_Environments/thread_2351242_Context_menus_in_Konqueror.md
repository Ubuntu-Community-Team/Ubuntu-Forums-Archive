---
title: "Context menus in Konqueror"
date: 2017-02-01
forum: Desktop Environments
---

### Post by thanuntu on 2017-02-01
Hi all,

This is definitely a common and recurring problem, and it is beyond me how it can keep creeping up every other version.

I recently upgraded from Ubuntu 12.04 to 16.04. In both cases I used Konqueror, which I find the best file manager out there (tried many). I have a problem with the context menus, in particular those doing compressions/extractions with ark. These are nowhere to be found, however, they' re there in Dolphin (screenshots).
Konqueror: [ATTACH=CONFIG]273469[/ATTACH]
Dolphin: [ATTACH=CONFIG]273468[/ATTACH]

Konqueror seems to think that this service menu is installed and activated (Settings -> Configure Konqueror -> File Management -> Services:
[ATTACH=CONFIG]273470[/ATTACH]

I have already tried the solution
```
sudo ln -s /usr/share/kde4/servicetypes/konqpopupmenuplugin.desktop /usr/share/kservicetypes5/
```
proposed for 15.10 ([https://www.kubuntuforums.net/showthread.php?69143-Ark-right-click-options-missing-in-15-10](https://www.kubuntuforums.net/showthread.php?69143-Ark-right-click-options-missing-in-15-10)), but apparently in 16.04 they corrected this, as this file already exists in both directories.

Any ideas?

On that note, can anyone please tell me why Konqueror (Help-About KDE) shows me "Platform version 4.4.16", while Dolphin (Help-About Dolhin) shows:
> **Version 15.12.13**
Using:
[LIST]
[*]KDE Frameworks 5.18.0
[*]Qt 5.5.1 (built against 5.5.1)
[*]The xcb windowing system
[/LIST]



What is Ubuntu using, KDE4 or KDE5?

---

### Post by thanuntu on 2017-02-06
I think I found a reply, but Canonical won't like it... I "down"graded to 14.04.

As if by magic all problems disappeared, including a pesky suspend issue that essentially crippled my laptop's function as a laptop.

I don't like to moan, particularly since Ubuntu is free and since I chose it over several other alternatives. However, I would like to politely suggest that users would be happier if new releases are rolled out without leaks their basic plumbing.

---

