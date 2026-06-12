---
title: "Updated my Pixelvision skin, now Steam will no longer open"
date: 2013-09-13
forum: Gaming &amp; Leisure
---

### Post by TheCadaver on 2013-09-13
[COLOR=#000000][FONT=verdana]OS is Ubuntu 13.04, running Steam with the Beta Opt-In turned on.

Due to a recent Beta client update that partially glitched current skins, the Pixelvision dev quickly released a new version of the skin. I installed it as I normally would, dragging the file to my Skins folder. I closed Steam and re-opened it for the changes to take effect, but nothing happened. Not even the "fetching updates" box or the Steam icon on the unity panel.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I poked around with the Skins file then, first by deleting the skin and reinstalling it. At this point, I would get the "fetching updates" box, but nothing else.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]My observations are as follows: "Steam" appears in the System Monitor, where I can click "End Process". It's using ~25% of my CPU. It also appears alongside a process labelled "tee", which disappears when the Steam process is killed/ended. Right-clicking the Steam icon in the Unity bar shows the Steam menu--Library, Friends, Community, etc. This appears even when the Steam process is killed, and clicking them does nothing. Restarting my computer does nothing. Can anybody help?

**Edit**: Fixed the problem with this; it should work for similar update-related problems, too.

[/FONT][/COLOR][COLOR=#000000]killall steam[/COLOR]
[COLOR=#000000]rm -Rf ~/.steam/steam/appcache[/COLOR]
[COLOR=#000000]steam[/COLOR]

---

### Post by TheCadaver on 2013-09-14
Bump.

---

### Post by DarkAmbient on 2013-09-14
Have you tried any of the solutions in the current Steam-issues threads? Like the one beneath this one (as i write)

---

### Post by TheCadaver on 2013-09-15
> **DarkAmbient said:**
> Have you tried any of the solutions in the current Steam-issues threads? Like the one beneath this one (as i write)

What do you mean?

---

### Post by DarkAmbient on 2013-09-15
Worth a shot?

[http://ubuntuforums.org/showthread.php?t=2174492](http://ubuntuforums.org/showthread.php?t=2174492)

---

