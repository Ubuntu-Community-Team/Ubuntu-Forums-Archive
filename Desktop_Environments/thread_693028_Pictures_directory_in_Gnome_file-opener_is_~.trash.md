---
title: "Pictures directory in Gnome file-opener is ~/.trash"
date: 2008-02-10
forum: Desktop Environments
---

### Post by Seymore on 2008-02-10
I deleted the Pictures directory usually in $HOME, as I wanted to have my pictures on a different drive. I made a symlink called Pictures to that drive. 

When I open files in eg. The Gimp, there is a Pictures folder in the sidebar, under Desktop and some drives, but this leads to ~/.Trash , not the symlink I made. How do I fix this?

PS: I am aware that I can add whatever directory I want in the bracked *below* the one where Desktop etc. is showing, but this wont do. These directories show every time I use the Gnome file-opener, but the Pictures directory should only show when I'm looking for pictures.

---

### Post by tcommbee on 2008-02-10
~/.config/user-dirs.dirs contains the relevant settings

---

