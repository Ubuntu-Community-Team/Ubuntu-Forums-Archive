---
title: "[SOLVED] Create new document - Templates problem"
date: 2008-09-10
forum: Desktop Environments
---

### Post by dangermouse28 on 2008-09-10
Have been trying to sort sort out the Create new document thingy in the Gnome context menu by creating a Templates directory and saving some blank documents in there.
However, it still doesn't work. It appears that my ~/.config/user-dirs.dir file isn't right.
When I alter the XDG_TEMPLATES_DIR to point to my Templates folder and save it, it gets overwritten the next time I restart Gnome!
Hardy Heron is driving me nuts - I didn't have any of these problems with any previous version of Ubuntu. (For the record, I've had them all and Gutsy was the best)


EDIT:
I fixed it!!!

In case anybody else is stumped by this, open the user-dirs.dir file in a text editor and find the XDG_TEMPLATES entry. Alter it to read:

XDG_TEMPLATES_DIR="$HOME/Templates"

Save and close and in a terminal, do:

$ sudo xdg-user-dirs-update

All done!

---

