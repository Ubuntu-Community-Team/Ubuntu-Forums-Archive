---
title: "SDLMame rom storage issue"
date: 2007-12-17
forum: Gaming &amp; Leisure
---

### Post by govee on 2007-12-17
I have Gutsy dual booted on my mame machine and moved my roms to a shared folder. For Gutsy it is SDA5. It is mounted on startup and I can access it and move files on and off it. I also use Wahcade as a frontend and I can create list from the setup but I can not execute the roms from either the frontend or a terminal. The roms can not be found (a synopsis of the terminal fialure) is the failure. Is there another ini file that needs to be change so that mame or sdlmame can find the roms? Or can I create symlinks to the roms and if so where do I store them?

thanks

---

### Post by disturbedite on 2007-12-17
i didn't like wahcade, it was too abstract.
i'd recommend kxmame w/ sdlmame.  (it requires compiling kxmame tho cuz the kxmame package in the ubuntu repo is too outdated to support sdlmame).
you can get instructions on how to do it here:
[http://ubuntuforums.org/showthread.php?p=3965888#post3965888](http://ubuntuforums.org/showthread.php?p=3965888#post3965888)

---

### Post by govee on 2007-12-18
thanks, but how does that help me. Wahcade can see the roms. Its sdlmame that can't.

---

### Post by disturbedite on 2007-12-18
well i guess should have specified, that was just a comment, not a possible solution to your problem...

sdlmame can see my roms fine.  i'd recommend checking your sdlmame config, perhaps you don't have it set to the correct rom directory.

---

### Post by govee on 2007-12-19
Thanks Disturbedite, I was concentrating on the name MAME and completley forgot about the SDLMame ini. Made corrections to the rom path and all works.

---

### Post by disturbedite on 2007-12-19
cool.  glad to help.

---

