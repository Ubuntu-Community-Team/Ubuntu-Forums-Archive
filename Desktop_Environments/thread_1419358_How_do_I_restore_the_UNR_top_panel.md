---
title: "How do I restore the UNR top panel"
date: 2010-03-01
forum: Desktop Environments
---

### Post by Mylorharbour on 2010-03-01
I backed up my wife's netbook and upgraded it from Hardy to Karmic moving the /home to a different partition. Karmic loaded a treat with the standard UNR desktop, however it appears that when I restored the backup data to the new /home partition it deleted the UNR top panel and replaced it with the classic Ubuntu top panel (Applications, Places, System etc) and the classic bottom panel showing workspaces etc. The centre of the desktop is still UNR with the menus at the left etc. How can I restore it to the standard UNR desktop?

---

### Post by spiderbatdad on 2010-03-01
I'm guessing that hidden directories in /home included .gconf and the like and contained files of user panel preferences from the Hardy installation.
Gconf has changed in Karmic to Gconf2, and sorting the .xml files across dozens of directories is a mess now. So can't offer a solution, just a bump to your thread and perhaps a hint at where to look.

---

