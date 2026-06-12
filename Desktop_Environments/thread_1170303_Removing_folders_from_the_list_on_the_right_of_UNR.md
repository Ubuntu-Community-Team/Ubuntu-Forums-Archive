---
title: "Removing folders from the list on the right of UNR"
date: 2009-05-26
forum: Desktop Environments
---

### Post by spaceballl on 2009-05-26
Hi all,

There's a list of folders on the right of the home screen of UNR. I'd like to hide a few. How do I do this?

---

### Post by linesma on 2009-05-26
The right side of the NBR interface is a mirror image of what is in your Nautilus Bookmarks menu.  To edit what is displayed there, open Nautilus.  You can do this by opening you home folder.  Goto your "Bookmarks" menu, and click on "edit bookmarks".  This will allow you to delete any that are listed there.  If you want to add a location to be displayed, navigate to where you want the bookmark to point to, and then goto Bookmarks--Add Bookmark or you can use the Ctrl-D keyboard shortcut.  This will then create a link to that location.

I hope this helps you out.

linesma

---

### Post by spaceballl on 2009-05-26
Thanks - this is helpful. However, this only lets me remove the four default bookmarks of "Documents", "Pictures", and "Videos". What about the "Network" link. Also, my windows xp partition is listed there too... Thanks!

---

### Post by linesma on 2009-05-26
Okay, I did a little digging and found a way that worked for me to remove those additional icons.  I was able to do it using a little program called Ubuntu Tweak.  You can download it here:  [http://ubuntu-tweak.com/downloads]("http://ubuntu-tweak.com/downloads")  Just download the .deb file, and double click on it.  It will install the program.  Open the program and go to "Desktop--Icons"  On that panel, it allows you to choose what is displayed.

There is a way to do it using the gconf-editor, but I could not find it.  The lack of customization options is why I run the NBR spin with the classic desktop enabled.

Hope this helps you out.

Mark

---

### Post by ertai on 2009-06-09
This will remove the favorites-menu:

Remove the menu in the menu editor and remove /usr/share/desktop-entries/Favorites.directory

When both don't exist then the menu won't appear.

---

