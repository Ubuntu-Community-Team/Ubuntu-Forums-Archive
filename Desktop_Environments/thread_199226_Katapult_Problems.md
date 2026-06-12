---
title: "Katapult Problems"
date: 2006-06-18
forum: Desktop Environments
---

### Post by [S|G] on 2006-06-18
Katapult works really great for applications that KDE detected and placed on the K menu automatically. This includes all KDE applications and some other such as skype, freeciv, blender... 

But the problem is, it doesn't seem to detect stuff that it didn't place on the menu automatically (i.e: gvim, dosbox), even though I can both run them directly from the terminal (they are /usr/bin) and also have placed shortcuts on K menu. 

How can I get those applications to be recognized by katapult?

Thanks!

---

### Post by Jucato on 2006-06-18
Unfortunately, Katapult's Programs catalog (where it gets the names of the programs) is based only on what's contained in the K Menu. So you either have to add those manually or refresh K Menu (so that the newly installed apps could be added) so they could be used in Katapult.

---

### Post by [S|G] on 2006-06-18
As I said, I have already placed them on K menu. Still, they don't work. How can I refreh it? I have already hit the save button some times, but still doesn't work.

Thanks!

---

### Post by Jucato on 2006-06-18
Oh I'm sorry, I must have skipped that last part.
To refresh Katapult, right-click on the Katapult icon on the system tray and click on Configure Katapult. Once the dialog pops up, just press OK, without modifying anything. This will refresh Katapult.

If you're running Katapult without the system tray option, launch Katapult (Alt+Space, or whatever you configured it to), and press Ctrl+C. This will give you the same menu as right-clicking on the Katapult icon in system tray.

---

### Post by [S|G] on 2006-06-18
Thanks a lot, that worked :)

---

