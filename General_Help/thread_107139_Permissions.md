---
title: "Permissions"
date: 2005-12-22
forum: General Help
---

### Post by TheOldGuy on 2005-12-22
When I updated to Firefox 1.5 I lost my old bookmarks.  I have them backed up but when I try to copy the backup file to overwrite the default bookmark file, I get an error saying I do not have permission to write to the directory.  Using the graphical interface, how do I become a super user or whatever is necessary to copy my backup?
Thanks

---

### Post by BathroomNinja on 2005-12-22
If you have installed Automatix, you can right click on the folder, then go to scripts, then use Natalis as root here.  Then you can copy it over.  if you haven't run Automatix, then the quickest way is to do it from the terminal using sudo.

---

### Post by TheOldGuy on 2005-12-22
Automatix has been used.  Right click on the folder with the backup or with the file I want to replace.  Excuse my ignorance but I'm really new to Ubuntu and Linux.

---

### Post by BathroomNinja on 2005-12-22
right click on the folder you want to replace.  After you do this, it will open up a new natalis window.  in that window, you ARE root and can do anything.  But only in THAT window.

---

### Post by TheOldGuy on 2005-12-22
I don't want to replace a folder, only the bookmarks.html file.  Anyway, when I right click on a folder and choose Open with Nautilis, the folder opens but "paste" is still grayed out.  Dragging and dropping still gives me the permissions error.

---

### Post by BathroomNinja on 2005-12-22
[QUOTE=TheOldGuy]I don't want to replace a folder, only the bookmarks.html file.  Anyway, when I right click on a folder and choose Open with Nautilis, the folder opens but "paste" is still grayed out.  Dragging and dropping still gives me the permissions error.[/QUOTE]


Correct, that's because you are trying to use both windows.  Remember that in the old one, you are not root.  You can either do everything in that 1 window, or you can open up 2 root windows and do the drag-n-drop.  So, first...

Close firefox.

Right click on the bookmarks.html file that you want to replace.  Use properties to rename the file to something like bookmarks.html.old.

Using the same window, go find the older bookmarks.html file that you want to use.  Right click, COPY.  Then, go back to the folder of the new bookmarks.html (the one now called bookmarks.html.old) and right click, PASTE.

---

### Post by TheOldGuy on 2005-12-22
I opened every folder with Nautilis.  It will not let me rename, paste or anything else in any of the folders.  Nautilis is not opening as root and Ubuntu doesn't allow logins as root (without modification) so how do I become root in the graphical interface?

FYI, my backup file is on a thumbdrive which is recognized without any problems.  I just have no write capability in /etc/mozilla-firefox/profile.

---

### Post by TheOldGuy on 2005-12-22
Should also add, my first try was just to use Import in Firefox.  However, I get the first screen, then click next and nothing happens so I can't get to my thumbdrive or anything else to import the bookmarks.

---

### Post by BathroomNinja on 2005-12-22
OK.  Can you copy the bookmars from the thunbdrive to your desktop?

If so, do that.  Next, using one of the root Natalis windows, RIGHT click on the profiles folder.  go to properties, then Permissions.  Write down the permissions you see.  Next, put a check in READ and WRITE for all 3 lines.
Close the permissions box.  Now, drag and drop the bookmarks into the folder.  (you did rename or delete the old bookmarks at this point right?)

---

### Post by TheOldGuy on 2005-12-22
[QUOTE=BathroomNinja]OK.  Can you copy the bookmars from the thunbdrive to your desktop?

If so, do that.  Next, using one of the root Natalis windows, RIGHT click on the profiles folder.  go to properties, then Permissions.  Write down the permissions you see.  Next, put a check in READ and WRITE for all 3 lines.
Close the permissions box.  Now, drag and drop the bookmarks into the folder.  (you did rename or delete the old bookmarks at this point right?)[/QUOTE]

I've tried to change permissions from a Nautilis window and cannot.  As I said before, I have no write privileges, no root privileges even from a Nautilis window.  That's the problem.  How do I get a root window?  Nautilis is not getting me there.

---

### Post by BathroomNinja on 2005-12-22
[QUOTE=TheOldGuy]I've tried to change permissions from a Nautilis window and cannot.  As I said before, I have no write privileges, no root privileges even from a Nautilis window.  That's the problem.  How do I get a root window?  Nautilis is not getting me there.[/QUOTE]


Did you right click on the profiles folder, then go to scripts, then 'root natalis here' ? (or something like that, I'm not at home at the moment)

---

### Post by TheOldGuy on 2005-12-22
Here's what I'm doing.  Go to Applications>Debian>Apps>System>Nautilis
This puts me in Home.  In the left panel I click on File System
Right click on /etc and Open with Nautilis
Right Click on mozilla-firefox and Open with Nautilis
Right click on Profiles and Open with Nautilis
Right click on Bookmarks.html
Rename, permissions, anything related to writing the file is grayed out.

Once again, opening with Nautilis does not give me root privileges.

---

### Post by TheOldGuy on 2005-12-22
[QUOTE=BathroomNinja]Did you right click on the profiles folder, then go to scripts, then 'root natalis here' ? (or something like that, I'm not at home at the moment)[/QUOTE]

When I right click, I see nothing related to "scripts."  Where should it be?

---

### Post by BathroomNinja on 2005-12-22
[QUOTE=TheOldGuy]Here's what I'm doing.  Go to Applications>Debian>Apps>System>Nautilis
This puts me in Home.  In the left panel I click on File System
Right click on /etc and Open with Nautilis
Right Click on mozilla-firefox and Open with Nautilis
Right click on Profiles and Open with Nautilis
Right click on Bookmarks.html
Rename, permissions, anything related to writing the file is grayed out.

Once again, opening with Nautilis does not give me root privileges.[/QUOTE]


OK, it looks like the root script did not install.  Terminal is going to be the quickest way to do this.  there are good instructions here:  [http://www.ubuntuforums.org/showthread.php?t=99004&highlight=firefox+path](http://www.ubuntuforums.org/showthread.php?t=99004&highlight=firefox+path)

I will try to walk you through in a few minutes.

---

### Post by BathroomNinja on 2005-12-22
OK, what guide did you follow to install Firefox 1.5?  Or did you use Automatix to do it?  Basically, the quickest way to do this, is to use the terminal, cd your way into the directory that contains the profile folder.  Then do: sudo chmod 777 profiles

Then drag and drop.

---

### Post by TheOldGuy on 2005-12-23
[QUOTE=BathroomNinja]OK, what guide did you follow to install Firefox 1.5?  Or did you use Automatix to do it?  Basically, the quickest way to do this, is to use the terminal, cd your way into the directory that contains the profile folder.  Then do: sudo chmod 777 profiles

Then drag and drop.[/QUOTE]

Thanks BathroomNinja.  I now have my old bookmarks.

---

