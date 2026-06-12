---
title: "How to change the default program for DVD movies?"
date: 2009-03-04
forum: General Help
---

### Post by reprobus on 2009-03-04
I am using xubuntu 8.10. When I put in a dvd movie player automatically loads up. I don't like movie player, I prefer VLC. How can I make VLC auto load instead of movie player?

---

### Post by 4Orbs on 2009-03-05
Open the Settings Manager, click on the Removable Drives and Media button, click on the Multimedia tab. Change the command of the Video CDs/DVDs to:
```

vlc --volume 512 %m
```

Each user account will need to set this for default vlc playback.

This will open vlc at full volume when a DVD is inserted. You can find other good stuff on this forum in the Multimedia & Video section. Look for the sticky post "Comprehensive Multimedia & Video How-To".

---

