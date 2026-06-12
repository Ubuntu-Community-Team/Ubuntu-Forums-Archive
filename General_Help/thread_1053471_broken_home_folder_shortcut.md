---
title: "broken home folder shortcut"
date: 2009-01-28
forum: General Help
---

### Post by pmcginley on 2009-01-28
suddenly if i click on places/home folder (or anywhere else that is a shortcut/bookmark to a nautilus window) i get this message:

could not open location 'file:///home/patrick'
no application is registered as handing this file

what's going on?  i can get a nautilus window if i click on 'computer' or a mounted external drive, and everything seems to be working, but all my shortcuts are broken.

what happened?

---

### Post by ajgreeny on 2009-01-28
Right click on the icon, go to Properties, choose the "Open With" tab, and there choose "Open Folder"  That should do it for you.

---

### Post by pmcginley on 2009-01-28
well, it's not an application launcher, it's the link to my home folder under 'places'.  the same thing happens if i click on 'desktop' or anything under 'shortcuts'.  if i right-click on any of them i get the same error message...

oh, and i take it back about being to click on a mounted external drive - same thing.  basically, the whole 'places' menu (except 'computer', luckily) is not working.

---

### Post by Chris_Sugden on 2009-02-05
It sounds like you have an old Nautilus bookmark that can no longer be reached.  I say Nautilus bookmark to show a difference between them and bookmarks in, say, Firefox.  Nautilus Bookmarks are saved links to a location; a file, an FTP site, or someplace like that.

If that is so, delete the old Nautilus bookmark by opening Nautilus any way you can.  (Clicking Place->Home Folder will do fine.)  Then you can use the Bookmarks menu item to edit your bookmarks for Nautilus.  Just Remove the offender.

---

### Post by pmcginley on 2009-02-12
just wanted to say thanks for your pointers - sorry, i've  been away for the last week and didn't see that last reply until now.  turns out it *was* a default application problem, as ajgreeny first suggested.  somehow the default application (ie, 'open with') for all shortcuts that should open with nautilus got changed to no action or program (i forget not what the exact wording was).  had to repoint them at nautilus - all's well now...

---

### Post by glomboi on 2009-05-09
I have a similar problem with my dad's computer.

He is running Ubuntu 9.04.

When I click the home folder launcher either in the Places menu or a launcher in the Panel it opens up in gedit with an error message:
> /home/username is a directory.
Please check that you typed the location correctly and try again.
When I drag and drop the launcher onto the desktop, however, it works fine.
There is now no "Open with..." Tab for launcher properties.

Any ideas?

Glomboi

---

