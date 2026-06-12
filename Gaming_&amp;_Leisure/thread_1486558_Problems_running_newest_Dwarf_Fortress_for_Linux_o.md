---
title: "Problems running newest Dwarf Fortress for Linux on 64-bit..."
date: 2010-05-18
forum: Gaming &amp; Leisure
---

### Post by COden6484 on 2010-05-18
So the newest version of Dwarf Fortress is now compiled for Linux support.  Version 0.31.04.  It was apparently compiled for 32-bit, and I'm having trouble getting it to run with graphics enabled.  I get the following message when it starts up:

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

I used getlibs to try to install the 32-bit version of that library, and it seemed to install it fine.  But the program never looks for it in /usr/lib32...  What can I do besides install the 32-bit version of Ubuntu? Which I don't want to do...

---

### Post by Perfect Storm on 2010-05-18
LD_LIBRARY_PATH=/usr/lib32 <binary>

---

### Post by COden6484 on 2010-05-18
> **Artificial Intelligence said:**
> LD_LIBRARY_PATH=/usr/lib32 <binary>

Thanks for the suggestion, tried that and still get the same error.  Dwarf Fortress is run from a script also, so I put export LD_LIBRARY_PATH=/usr/lib32/ in the script and still same error.

---

### Post by Perfect Storm on 2010-05-18
Try this instead. Copy the "complaining" libs to DFs libs folder instead (df_linux/libs). Eventually point LD_LIBRARY_PATH=libs

---

### Post by COden6484 on 2010-05-18
I was told on the Dwarf Fortress boards that it's not an error that should be worried about.  Since this is the newest version and has the merge from last version to use SDL it's broken right now.  Apparently no one is able to use graphical tilesets currently.  I've changed the font to Mayday's to give it a graphical look, and it works fine for now.  They weren't sure why it was even looking at that library since it shouldn't need the GVFS.  So I guess we can consider this solved for now since there's no fix really.

Thanks for the help though! I appreciate it!

---

