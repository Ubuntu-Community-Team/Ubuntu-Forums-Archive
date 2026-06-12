---
title: "Can't open file with file browsers other than Nautilus windows in 11.04"
date: 2011-05-10
forum: Desktop Environments
---

### Post by karth on 2011-05-10
Hi,

I'm facing a crippling issue in terms of usability in Ubuntu since the last update. I chose to **update** my 10.10 setup toward 11.04 the day after it went out.

Since then, I'm unable to open a file (by clicking or double-clicking) using any file browser other than from a regular Nautilus window.

e.g.: The "Files and Directories" shortcut in the unity dock is correctly listing the files, but clicking any of them results in a failure, and a message saying that "This is not a directory" (of course! it isn't!).

It also occurs when double clicking an attached file in Evolution Mail Client, and a lot of other places.

Please, see the attached picture displaying the actual error message.

Has anybody any clue of what's going on?

---

### Post by Krytarik on 2011-05-10
Try removing "~/.local/share/applications/mimeapps.list" and ".../mimeapps.cache" after backing them up before.

Greetings.

---

### Post by karth on 2011-05-10
Unfortunately, that doesn't seem to help. I moved the files away, and even logged out and then back in to restart nautilus, the error is still present...

---

