---
title: "Oneiric terminal font setting in Gnome"
date: 2011-10-17
forum: Desktop Environments
---

### Post by huangyingw on 2011-10-17
Hello,
   I have recently upgraded to Ubuntu Oneiric.
   The most unsatisfactory thing is that the font of terminal in Gnome.
   Is there any configuration file, which could directly update the terminal font in Gnome ?
   I have googled out some messages about "Gnome tweak tool". But the faults of this tool, are that, I don't know which option is directly related to terminal font, and after changing, if unsatisfactory, how could I restore the default setting ? For I found no choice of "Ubuntu" in Advanced Settings.

---

### Post by mcduck on 2011-10-17
If you have the Ubuntu fonts, like you should have by default, then sure they should appear in Gnome Tweak Tool.

...and the font setting that affects terminals would be the Monospace font.

Anyway, if that doesn't work for you for some strange reason, you can just as well define your terminal font directly in Gnome-terminal. Just right-click anywhere in the terminal window and select Profiles->Profile Preferences (or Edit->Profile Preferences from the menu), and on the General-tab unmark the "Use the system fixed width font"-option and select your own font from the dropdown box.

---

### Post by huangyingw on 2011-10-18
> **mcduck said:**
> If you have the Ubuntu fonts, like you should have by default, then sure they should appear in Gnome Tweak Tool.

...and the font setting that affects terminals would be the Monospace font.

Anyway, if that doesn't work for you for some strange reason, you can just as well define your terminal font directly in Gnome-terminal. Just right-click anywhere in the terminal window and select Profiles->Profile Preferences (or Edit->Profile Preferences from the menu), and on the General-tab unmark the "Use the system fixed width font"-option and select your own font from the dropdown box.
Thanks, I prefer the "Gnome-terminal" solution, and it works.

---

### Post by sanso on 2011-10-20
> **huangyingw said:**
> Thanks, I prefer the "Gnome-terminal" solution, and it works.
Hey all, thanks for this one. I wasn't aware that the slightly more advanced settings had been moved out of the default configuration dialogue.

Huangyingw, If you don't have a specific reason to limit your change just to the terminal, I highly recommend using gnome-tweak-tool to set your font, as that will apply for all applications that use a monospace font, not only the terminal.

---

### Post by huangyingw on 2011-10-25
> **sanso said:**
> Hey all, thanks for this one. I wasn't aware that the slightly more advanced settings had been moved out of the default configuration dialogue.

Huangyingw, If you don't have a specific reason to limit your change just to the terminal, I highly recommend using gnome-tweak-tool to set your font, as that will apply for all applications that use a monospace font, not only the terminal.
Yes, thanks. I&#12288;am almost satisfied with the font setting in Oneiric, except the terminal.
For I always use VIM, and in terminal, the characters seem to overlap, and thus looks terrible and tiresome. So the solution only targeted at terminal, is good enough for me.

---

