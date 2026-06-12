---
title: "Oversized bootsplash and console fonts"
date: 2006-08-11
forum: Desktop Environments
---

### Post by linbetwin on 2006-08-11
Bootsplash is too large for my 1024x768 screen. I know this can be fixed with "vga=791" added to the GRUB menu.list, but that doesn't fix the console fonts. When my screen is filled with commands and such I can't see the bottom line - the very line where I am supposed to write commands.

This bug or feature or whatever it is drives me crazy. It was present during Breezy development but was fixed in Breezy final. It reared its head again during Dapper development but it wasn't fixed anymore.

Does anybody have any solutions?

---

### Post by linbetwin on 2006-08-12
Is no one else experiencing this? Try switching to a console and issue some commands, untill the screen fills up. Then you won't be able to see the bottom line, the one in which you're supposed to write.

---

### Post by clarjon1 on 2007-12-14
Not sure if it would work, but perhaps if youcould try running the setupcon command, which should be able to let you set the console font and keyboard layout.
It appears to be a part of the console-tools package.

---

