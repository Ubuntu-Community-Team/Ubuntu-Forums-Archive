---
title: "How to edit the Gnome places menu?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by Xgkkp on 2005-04-12
Hi, I have a simple request, the 'places' menu can be added to by using the gnome "open file" dialogue, but I would like to know the location it stores the settings/links, so that I might be able to edit them manually (It says win_c / win_d and I would like to rename them to more user-friendly alternatives).

Thanks!

---

### Post by turchinc on 2005-04-20
the .gtk-bookmarks file in your home directory is the key...

---

### Post by Sam on 2005-04-20
This file stores only the URI. I don't think there is a way to rename the link. But you can make a symlink somewhere with a user-friendly name that link to the folder of your choice and then add it to the .gtk-bookmarks file.

---

### Post by blakzer0 on 2008-03-04
Just make a space after the file name and type what you want it to display as.

Example:
file:///home/user/Documents Someone Elses Documents

---

### Post by chip_munk on 2008-03-04
Excellent. Thanks for that.

---

### Post by lngndvs on 2008-03-24
This is very helpful. So when I add more than about 5 or 6 directories (folders) to .gtk-bookmarks, they are no longer listed directly on the menu, but apparently as a consequence of the number of links, they are listed in a folder "Bookmarks".  How can I organize to see them right on the menu itself?  

Alan:)

---

### Post by rainwalker on 2008-03-25
After a certain number of items, they're placed in the Bookmarks menu so the Places menu doesn't get insanely long
Also, to edit Places you can open a file browser window and in the pane on the left choose the "Places" view and then drag/drop the folders/URLs/whatever into that side bar

---

### Post by AbtZ on 2008-04-23
> **rainwalker said:**
> After a certain number of items, they're placed in the Bookmarks menu so the Places menu doesn't get insanely long
Also, to edit Places you can open a file browser window and in the pane on the left choose the "Places" view and then drag/drop the folders/URLs/whatever into that side bar
As it stands now, this limit is set stupidly low by default at >5. From what I have gathered you will have to recompile gnome-panel yourself to change this.

Who do I talk to so this default can change to something better, perhaps 10 or 15?

---

