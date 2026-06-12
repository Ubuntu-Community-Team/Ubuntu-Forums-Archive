---
title: "remove target on [ctrl] press"
date: 2008-11-20
forum: Desktop Environments
---

### Post by maphew on 2008-11-20
Hello,

Several ubuntu versions ago, 5.10 or 6.04 I think, under the System > Preferences menu there was an option to enable drawing of concentric circles around the mouse pointer when the [ctrl] key was pressed. I don't want this anymore, it seems to slow down operations like repetitive [ctrl][arrow][arrow]... However the preference menu for this setting has vanished. How do I remove it?

I'm now using Intrepid Ibex, 8.10.

thanks :)

----------------------
The answer is to look under mouse preferences, not keyboard. Doh!

   Preferences -> Mouse
   Uncheck - Show position of mouse when ctrl is pressed

Thanks Sam! [http://answers.launchpad.net/ubuntu/+question/52554](http://answers.launchpad.net/ubuntu/+question/52554)

---

### Post by ohzopants on 2008-11-20
I think it's been placed under the "accessibility" section of the settings.

---

### Post by maphew on 2008-11-23
I found a raft of keyboard settings under "System > Preferences > Assistive Technologies > Keyboard Accessibility > Layouts > Other Options" but they all seem to be about keyboard remapping or key position (changing caps-lock into an extra ctrl key, etc.). Is that where you were thinking of or is there another place I should be looking?

---

### Post by ohzopants on 2008-11-25
I went looking for this setting last night and I couldn't find it in any of the settings dialogs.  I also tried to find it in gconf-editor and it doesn't appear to be there either.

You may want to consider filing a bug report for this.

---

