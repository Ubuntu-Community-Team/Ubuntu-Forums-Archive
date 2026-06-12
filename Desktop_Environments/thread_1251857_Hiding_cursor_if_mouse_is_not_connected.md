---
title: "Hiding cursor if mouse is not connected"
date: 2009-08-28
forum: Desktop Environments
---

### Post by T. Terhoeven on 2009-08-28
Hey,

I have written an [information screen system based on PHP]("http://www.drterhoeven.de/entrada/screen.php"), to be displayed with Mozilla Firefox. The cursor should be hidden, but the screen refreshes every 15 seconds and as it is refreshing the cursor is shown. Is it possible to hide the cursor if there is no mouse connected (or permanently)?

Tobias

//edit: SOLVED, installed unclutter and set "unclutter -display :0.0 -grab" as startup application...

---

