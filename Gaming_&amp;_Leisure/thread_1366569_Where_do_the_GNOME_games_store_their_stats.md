---
title: "Where do the GNOME games store their stats?"
date: 2009-12-28
forum: Gaming &amp; Leisure
---

### Post by Spreadsheet on 2009-12-28
I don't have access to a computer running GNOME right now, but if you get a high score, will the other users see your high score?

---

### Post by Sindwiller on 2009-12-28
Most likely in ~/.GAME_NAME/* (~/ is the respective home directy of the user you're logged in as at the moment). Somewhere in there.

Basically, every application stores user-related information in dotted folders, e.g. your KDE configs are stored in ~/.kde, and so on.

---

### Post by Spreadsheet on 2009-12-28
This seems to be a bug. Are there any plans to change this to store the data in a folder accessible by everyone (/usr/games maybe?)

---

### Post by Sindwiller on 2009-12-28
> **Spreadsheet said:**
> This seems to be a bug. Are there any plans to change this to store the data in a folder accessible by everyone (/usr/games maybe?)

/usr is readable but not writeable by everyone.

I said *most likely* - they might've found a better solution. :P

---

### Post by Spreadsheet on 2009-12-28
I see. Thanks for explaining.

---

