---
title: "Freeciv SDL client in Ubuntu?"
date: 2008-01-11
forum: Gaming &amp; Leisure
---

### Post by jazzbum on 2008-01-11
I'm new to Linux so please be kind. :KS I want to try out the UI on the Freeciv SDL client and am having problems running it.  I installed it from getdeb.net with the data and server files.  Now when I go into the terminal and type civ I get the following message:

[I]2: Using Video Output: x11
0: Could not open font: /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
0: No usable default theme found, aborting!
[/I]
Now I know that the GTK version works fine, but I am really curious what the difference is in the interface I would also like to learn something new about SDL.  Any thoughts or help appreciated.

---

### Post by matthewcraig on 2008-01-11
Just as a kind of general good idea, you might be better served by waiting until the new Freeciv SDL client is in the official Ubuntu repositories.  Then, you will know the package will work with your desktop and that it had some amount of testing.

You'll have to have some patience, but I find it is better to wait and get a clean install, than it is to install applications as root user and muck up the environment.

---

### Post by zmeuka on 2008-02-02
> **jazzbum said:**
> [I]2: Using Video Output: x11
0: Could not open font: /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
0: No usable default theme found, aborting!
[/I]


There is a bug in freeciv SDL interface: theme config does not support absolute paths (at least for fonts). You can "fool" it:

root@machine# cp /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf /usr/share/games/freeciv/themes/gui-sdl/human/

then edit /usr/share/games/freeciv/themes/gui-sdl/human/theme.themespec
look for the line that begins with *font_file* and change it to:
**font_file         = "themes/gui-sdl/human/DejaVuSans.ttf"**

try to run civ and it will be OK now.

---

