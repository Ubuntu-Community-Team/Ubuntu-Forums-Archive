---
title: "I found out how to disable annoying F1 help activation"
date: 2009-11-06
forum: Desktop Environments
---

### Post by leafw on 2009-11-06
1. Go to System - Preferences - Keyboard Shortcuts
2. Create a new shortcut. Name it 'do nothing', and write 'false' (without quotes) in the "command" field. Push ok.
3. Scroll to the bottom of the list and find your new command. Click on the "Disabled", on the right, and push F1.

Now F1 is linked to /bin/false, a command whose "man false" says: "Do nothing, successfully."

Now no Gnome application (like nautilus) will open the help window ever again when accidentally pushing F1.

---

### Post by damko on 2010-08-20
amazing trick. Thank you!

---

