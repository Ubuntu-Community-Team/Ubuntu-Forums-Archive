---
title: "Freeciv crashing after clicking on any button."
date: 2007-12-09
forum: Gaming &amp; Leisure
---

### Post by holihue on 2007-12-09
Freeciv is crashing when I click on any button in the menu, it happens every time, and it does not appear randomly.

What is wrong? 
Freeciv worked for me before.



Thanks

---

### Post by Vadi on 2007-12-09
Launch it from the terminal, and when it crashes, paste the output?

---

### Post by holihue on 2007-12-09
```
civ
```
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
1: Error calling Mix_OpenAudio
1: Plugin sdl found but can't be initialized.
2: No real audio subsystem managed to initialize!
2: Perhaps there is some misconfiguration or bad permissions
2: Proceeding with sound support disabled
Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory
Killed
```

And:

```
civ -d 3
```

```
3: log started
3: USER username is hk
3: Data path component (0): .
3: Data path component (1): data
3: HOME is /home/hk
3: Data path component (2): /home/hk/.freeciv
3: Data path component (3): /usr/share/games/freeciv
3: settings file is /home/hk/.civclientrc
3: Reading registry from "/home/hk/.civclientrc"
3: Booting help texts
3: Reading registry from "/usr/share/games/freeciv/helpdata.txt"
3: Booted help texts ok
3: tilespec file is "/usr/share/games/freeciv/amplio.tilespec".
3: Reading registry from "/usr/share/games/freeciv/amplio.tilespec"
3: tile sizes 96x48, 9672 unit, 1520 small
3: Reading registry from "/usr/share/games/freeciv/amplio/terrain1.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/terrain1.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/terrain2.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/terrain2.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/tiles.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/tiles.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/fog.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/fog.spec:
3:   unused entry: spec.artists
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/small.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/small.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/units.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/units.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/flags.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/buildings.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/wonders.spec"
3: Reading registry from "/usr/share/games/freeciv/misc/space.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/space.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/techs.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/techs.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/treaty.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/treaty.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/nuke.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/nuke.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/explosions.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/explosions.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/ancientcities.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/ancientcities.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/medievalcities.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/medievalcities.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/moderncities.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/moderncities.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/select.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/select.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/amplio/grid.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio/grid.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/cursors.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/cursors.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/colors.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/colors.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/overlays.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/overlays.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/citybar.spec"
3: Unused entries in file /usr/share/games/freeciv/misc/citybar.spec:
3:   unused entry: file.gfx
3: Reading registry from "/usr/share/games/freeciv/misc/shields.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/icons.spec"
3: Unused entries in file /usr/share/games/freeciv/amplio.tilespec:
3:   unused entry: tilespec.is_mountainous
3:   unused entry: tilespec.is_full_citybar
3: finished reading "/usr/share/games/freeciv/amplio.tilespec".
3: Initializing sound using stdsounds...
3: Reading registry from "/usr/share/games/freeciv/stdsounds.soundspec"
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
1: Error calling Mix_OpenAudio
1: Plugin sdl found but can't be initialized.
2: No real audio subsystem managed to initialize!
2: Perhaps there is some misconfiguration or bad permissions
2: Proceeding with sound support disabled
3: No sound file for tag music_start (file -)
3: Neither of tags music_start or (null) found
Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory
3: color system booted ok.
3: Reading registry from "/usr/share/games/freeciv/misc/treaty.spec"
3: Reading registry from "/usr/share/games/freeciv/misc/small.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/terrain1.spec"
3: Reading registry from "/usr/share/games/freeciv/misc/overlays.spec"
3: Reading registry from "/usr/share/games/freeciv/misc/space.spec"
3: Reading registry from "/usr/share/games/freeciv/misc/cursors.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/nuke.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/explosions.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/tiles.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/units.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/select.spec"
3: Reading registry from "/usr/share/games/freeciv/misc/citybar.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/moderncities.spec"
3: Using alternate graphic "city.size_0" (instead of "path.turns_0") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_1" (instead of "path.turns_1") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_10" (instead of "path.turns_10") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_2" (instead of "path.turns_2") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_20" (instead of "path.turns_20") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_3" (instead of "path.turns_3") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_30" (instead of "path.turns_30") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_4" (instead of "path.turns_4") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_40" (instead of "path.turns_40") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_5" (instead of "path.turns_5") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_50" (instead of "path.turns_50") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_6" (instead of "path.turns_6") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_60" (instead of "path.turns_60") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_7" (instead of "path.turns_7") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_70" (instead of "path.turns_70") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_8" (instead of "path.turns_8") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_80" (instead of "path.turns_80") for sprite "path.turns_tens[i]".
3: Using alternate graphic "city.size_9" (instead of "path.turns_9") for sprite "path.turns[i]".
3: Using alternate graphic "city.size_90" (instead of "path.turns_90") for sprite "path.turns_tens[i]".
3: Reading registry from "/usr/share/games/freeciv/misc/colors.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/grid.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/terrain2.spec"
3: Reading registry from "/usr/share/games/freeciv/amplio/fog.spec"
3: The tileset doesn't specify prefered themes or none of prefered themes can be used. Using system default
Killed
```


I got nothing in the terminal after clicking a button.

---

### Post by Vadi on 2007-12-09
No idea. Try filling a bug report?

---

