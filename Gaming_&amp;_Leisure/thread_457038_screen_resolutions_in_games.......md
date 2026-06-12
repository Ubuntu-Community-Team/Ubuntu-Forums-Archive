---
title: "screen resolutions in games......"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-05-28
hello.
this my seem like a silly question, but ive been messing around installing games, ever since i found these loki installers (great little things) anyway the question is that the resolution that is best for my monitor is 1280x800 (i have edited the /etc/X11.xorg.config so that it starts at this resolution) but some games dont support that resolution, i noticed with doom 3 that if i changed the resolution in game to the nearest setting, when i restart the game to apply the changes it doesnt display in full screen (the resolution im talking about is 1152x864) so would i need to edit xorg.config and include all the resolutions i may want to run a game at ? at the moment the resolutions i have in xorg.conf are as follows - "1280x800" "1024x768" "800x600" "640x480" i had to include the 1280x800 so i didnt have to keep going into the nvidia settings to change it every time i started the pc. any help will be appreciated, i wanted to ask before i edit xorg.config so i dont kill my system and have to do a re-format :D
cheers

---

### Post by Hobo Joe on 2007-05-28
That's not a very common resolution, you'll need to change the resolution in Ubuntu to a common one, 1280x900, or 1280x1024 would probably be best.

The reason it's not fullscreen is becuase the resolutions have different aspect ratios, so the only way to make the game not appear distorted is to make it not fullscreen.

---

### Post by techno-mole on 2007-05-28
i know its not very common, but its the best for my monitor.
my monitor wont display at the resolutions you put in your post.
maybe then i should use a different resolution ll round ? such as  1152x864 
anyway cheers, ill have a play around and see what happens.

---

