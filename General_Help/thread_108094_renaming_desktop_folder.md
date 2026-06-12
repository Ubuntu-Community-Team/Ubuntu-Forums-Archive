---
title: "renaming desktop folder"
date: 2005-12-25
forum: General Help
---

### Post by everdred on 2005-12-25
Is it possible to rename the desktop folder (within ~/) and have it remain my the folder that displays items on my desktop?

And before someone asks the inevitable (because someone always does :)), I'd like the "Desktop" folder to be called "desktop" for typing simplicity.

---

### Post by 23meg on 2005-12-25
Go to your home folder in the terminal and type ```
ln -s Desktop desktop
```This will create a symlink called "desktop" which will let you type "desktop" instead of "Desktop".

---

### Post by Sutekh on 2005-12-25
This is kinda not what you were asking, but when you mentioned ease of typing I had to chime in.

It's possible to make your home directory your desktop directory, using the configuration editor, under apps -> nautilus -> preferences and then check desktop_is_home_dir.  This sets /home/user as the desktop folder, instead on /home/user/Desktop.

Like I said; for ease of typing.

---

### Post by everdred on 2005-12-25
**23meg**, that's perfect. Thanks, I wouldn't have thought of that! :D

**Sutekh**, thank you too for the suggestion, but that's not quite what I'm looking for. I saw some back-and-forth on a wiki or mailing list or somewhere about a suggestion re: making this the default, and... nah, no thank you. :) I only really use the desktop as my temporary dump space, anyhow.

---

### Post by Sutekh on 2005-12-25
I agree, I like having a separate desktop folder.  But just in case y'know.

---

### Post by 23meg on 2005-12-25
Cool, glad it works for you. Symbolic links work wonders in such situations; type ```
man ln
``` to learn more.

---

