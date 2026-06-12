---
title: "keyboard shortcuts config file"
date: 2009-06-04
forum: General Help
---

### Post by e49d9 on 2009-06-04
where does the os keep the config file that contains all the custom keyboard shortcuts?

---

### Post by e49d9 on 2009-06-04
?

---

### Post by e49d9 on 2009-06-04
i'm not sure if i'm in the wrong forum or if what i am asking is unclear so here is my attempt to clarify.

what is the name of the file that holds the "Standard Keyboard Shortcuts" and the "Global Keyboard Shortcuts" that i define in the System Settings application?  additionally i would like to know where the "Application Launcher Menu Settings" are stored.

i'm not sure it makes a difference or not which desktop i am using, but it's kde.

---

### Post by majkiw on 2009-07-29
User defined shortcuts are stored in gconf configurations in:
~/.gconf/apps/metacity/

---

### Post by Zorael on 2009-07-29
> **majkiw said:**
> User defined shortcuts are stored in gconf configurations in:
~/.gconf/apps/metacity/
That's a GNOME answer - he said he's using KDE.

You'll probably find what you're looking for in **~/.kde/share/config/**; that's where most of KDE apps' user-specific settings are stored. I'm not sure which one in particular houses global shortcuts (khotkeysrc?). One way would be to open the directory in Dolphin and sort files after date changed, then pop up System Settings and make a change to the hotkeys and see which files get modified.

Or just browse the files in a text editor and deduce context by content.

---

