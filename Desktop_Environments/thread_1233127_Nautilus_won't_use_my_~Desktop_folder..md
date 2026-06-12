---
title: "Nautilus won't use my ~/Desktop folder."
date: 2009-08-06
forum: Desktop Environments
---

### Post by TiMBuS on 2009-08-06
So recently I installed a new hard drive to replace an old one that had my /home partition on it. To make the switch I made an ext4 partition on my new disk the same size of my old /home, and then just copied everything over with nautilus (In retrospect maybe cp -a or even making a disk image would have worked better). 
Anyway, in the process of doing this I guess I somehow managed to forget to copy over ~/Desktop to my new disk. I didn't even notice until I booted ubuntu with my new disk mounted as /home. Now because of this, nautilus will only use my home folder for the desktop. I made a new Desktop folder and restarted nautilus but it didn't work. I checked gconf-editor and made sure desktop_is_home_dir is false. I've tried grepping all my config files, searching gconf, fiddling with nautilus settings, and I've pushed my google-fu to its limits. I'm at a loss here.

Does anybody know how to make nautilus use my ~/Desktop folder again?

---

### Post by mcduck on 2009-08-06
Press Alt-F2 and run "gconf-editor" (or start it from a terminal), then use it to browse to apps/nautilus/preferences, and deselect the "desktop_is_home_dir"-key.

---

### Post by TiMBuS on 2009-08-06
> **mcduck said:**
> Press Alt-F2 and run "gconf-editor" (or start it from a terminal), then use it to browse to apps/nautilus/preferences, and deselect the "desktop_is_home_dir"-key.

Thanks but I've already tried that, I mentioned it in my OP (sorry if it's a bit wordy but I wanted to make sure the issue + possible causes were described properly)

---

### Post by wojox on 2009-08-06
Edit ~/.config/user-dirs.dir and change:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by TiMBuS on 2009-08-06
> **wojox said:**
> Edit ~/.config/user-dirs.dir and change:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

Oh thank you so much, that fixed it :D. I spent days trying to fix this, and it was something so simple. I just couldn't find it.

Wow I can even move my desktop somewhere else now. Fantastic.

Thanks again!

---

