---
title: "What in 8.10 could possibly cause this?"
date: 2009-04-30
forum: General Help
---

### Post by Infinyte on 2009-04-30
I installed 8.10 on an older computer (which I don't currently have the specs for) for a friend.  But every time there is a drop-down menu box displayed, (Such as the "Prefix" one on this Post New Thread page), it will open and instantly close.  You can keep it open by holding down, then dragging your mouse to the selection and letting go.  But even that won't work ALL of the time.  I'm not finding anything about it on the forums or on Google (But maybe I'm not using the right search terms...), anyone got a clue as to what this could possibly be?

---

### Post by 4Orbs on 2009-04-30
This happened to me when I was running 8.10. In my case it was caused by a particular theme I had installed... don't remember exactly which theme, but it had "crystal" in it's name. It required the latest SVN Murrine engine to run properly, but even when I installed the specified engine it still didn't work. Even right-clicking on a folder, I had to hold down the button to get the menu to stay open.

---

### Post by mb_webguy on 2009-04-30
It could be due to corrupted configuration files.  Try creating a new profile by starting Firefox from the terminal with "firefox -profileManager".  If that works, import your bookmarks and password (using the Password Exporter extension) to the new profile.

---

### Post by Infinyte on 2009-05-01
Hmm.. Well they haven't installed any additional themes, and it doesn't only happen in Firefox, it's any dropdown menu that you try to use, even ones in various setting menus in Ubuntu.

---

### Post by gsp8181 on 2009-05-01
Just a side note, If you are on an older computer, you might want to consider using Metacity as your window manager, speeds things up a bit

---

