---
title: "Icons freaking out"
date: 2009-01-18
forum: General Help
---

### Post by PoopLoops on 2009-01-18
I tried to get icons in my panel for programs such as Tuxguitar.  Found some online, put them in my icons folder (all in /usr/share/icons/hicolor/scalable/apps) as .png files.  It worked!  And now all my other icons are just dead.  I mean desktop icons for files, folders, anything, even for things like buttons in Rhythmbox.  It's all gone.  I right click and hit "properties" and it only opens the folder I'm looking at, not the properties of that folder...

How could I mess up big time like that?  All I did was change the permissions to let me download icons into the folder instead of having to download to Desktop and then sudo mv /blah.

---

### Post by metallicamike on 2009-01-18
delete them and use system>preferences>appearance and install them with that. good luck!

---

### Post by PoopLoops on 2009-01-18
Install what?  When I do that, a browsing window is opened asking me to select the file, but it starts in my home folder.  Where am I supposed to navigate?

EDIT:  Oh, I found my ".themes" folder, duh.  But there's nothing in there...

And another thing, if I open Nautilus as root, all the icons are there, which I guess would make sense if I only messed up my account settings.

EDIT 2:  Found a "themes" folder in /usr/share/themes but all the folders inside are empty.  Any files I try to use (by viewing "all files" instead of "theme packages") don't work.

EDIT 3:  Okay, now I installed a custom theme from the internet.  Some icons have been restored, such as the "show desktop" icon, but they are still mostly gone.  I am able to change the icons for individual folders, but I am not going to sit there and changing them one by one.  I'm stumped!

---

### Post by PoopLoops on 2009-01-18
Okay, got it fixed.

It ended up being an issue of permissions.  What happened was I changed "Group" from "root" to "[my user account]" for some of the folders in order to be able to move my custom icons in there without having to sudo anything.  That screwed up everything that was part of the "root" group I am assuming, that's why they couldn't access it and that's why I had no icons.

Thank you, and good night. :)

---

