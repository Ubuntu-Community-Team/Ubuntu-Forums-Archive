---
title: "How do you run VisualBoy Advance?"
date: 2009-06-11
forum: Gaming &amp; Leisure
---

### Post by SilentOcean700 on 2009-06-11
Im new to ubuntu. (running on hardy heron version)

i installed a visualboy package manually, supposedly, according to what my computer said, it was installed. i think it was supposed to show up in the 'games' section, because thats what happened when i installed zsnes-it showed up right away. 

but visualboy advance wont show up anywhere. i did a search, but i only found parts of the package scattered off into different folders, like usr/bin/man1/ etc, and none of them will even run.

i tried to muse terminal's sudo-apt command but all i get is 'command not found' whenever i try...

how do i run the emulator?

---

### Post by hessiess on 2009-06-11
Use mednafen insted.

---

### Post by mcduck on 2009-06-11
VBA is a command-line program and has no graphical user interface.

I recommend installing VBA-Express which is a nice graphical frontend for VBA.

---

### Post by del_diablo on 2009-06-11
Let me guess, you installed this:
*visualboyadvance
Which does not contain the frontend.......... aka no GUI, thus no entry in the menu.
Go back into synaptic and start typing in visual so you get down to where it is and then mark the entry under it named "visualboyadvance-gtk"

---

