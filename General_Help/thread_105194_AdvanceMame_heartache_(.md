---
title: "AdvanceMame heartache :("
date: 2005-12-17
forum: General Help
---

### Post by Mosey on 2005-12-17
Hi everybody.

So I setup and installed both AdvanceMame and AdvanceMenu because I prefer working with a good GUI.

On my first run I got this error:

[I]admin@ubuntu:~/Desktop/advancemenu-2.4.12$ advmenu
AdvanceMENU - Copyright (C) 1999-2004 by Andrea Mazzoleni
Emulator 'advmame' without rom files, ignoring it.
No working emulator found. Adjust the `emulator' options in your configuration
file. These options are documented in the `advmenu.txt' file.[/I]

Apparently it ignores any emulators without Rom files in them. Okay...i'll bite...I found and installed a Rom and ran it again:
[I]
admin@ubuntu:~/Desktop/advancemenu-2.4.12$ advmenu
AdvanceMENU - Copyright (C) 1999-2004 by Andrea Mazzoleni
Unable to initialize the video driver. The errors are:
fb: Unsupported in X.[/I]

No dice.

It says in the documentation that it is in fact compatable with X. So what gives?

Thanks in advance for any help.

---

### Post by Mosey on 2005-12-18
Bump-a-dump!

---

### Post by Mosey on 2005-12-18
Apparently in Ubuntu and Kubuntu one needs to disable framebuffering...

I have no friggin clue how to do this...if anyone...ANYONE...can help me, i would endlessly appreciate it.

---

### Post by Mosey on 2005-12-18
bumpppppppppppppppppppp

---

