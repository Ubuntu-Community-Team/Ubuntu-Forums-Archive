---
title: "Broken search.. due to beagle?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by fletch on 2006-06-02
After uninstalling beagle, and attempting to use the normal search function within the gnome menu, I get this problem before it loads up:

> 
**Could not load menu item**

Details: Error reading file 'file:///usr/share/applications/beagle-search.desktop': File not found


I searched for beagle uninstall methods throughout the forum and google, but no such luck. Any takers?:confused:

---

### Post by TrD on 2006-06-02
The same thing has happened to me. 
I uninstalled beagle through synaptic, and now when I press ctrl+f to perform a search I get this message:

"Unable to connect to Beagle daemon"

---

### Post by Toby on 2006-06-02
Beagle search was integrated with GNOME in the new release, if I recall correctly... 
It would certainly explain the errors.
.
Update: Double-checked, and indeed, Beagle was integrated as a part of the Nautilus search in 2.14.
GNOME is configured to search with beagle first, then fall-back to the old search if it can't find it.

---

### Post by fletch on 2006-06-02
Thanks for the heads up on that, Toby.

From what i've gathered in the forums about beagle, its file-indexing capabilities come with a price. I've read about performance issues of the OS and oddities with its cache size.

My point with all of this is, should I just keep it installed? I only had it installed for a maximum of a few minutes, couldn't find how to operate it, so I decided to uninstall it after reading about its problems in the forums. I've also read however some of these things were repaired with updates.

EDIT: Installed it again, search works, or so i thought. I believe its only set to search my home folder, where i want the option to scan the whole file system if need be. Is there any other options or fixes for this? I'm assuming its a bad idea to index my whole file system.[-X

---

### Post by bjc on 2006-06-02
> EDIT: Installed it again, search works, or so i thought. I believe its only set to search my home folder, where i want the option to scan the whole file system if need be. Is there any other options or fixes for this? I'm assuming its a bad idea to index my whole file system.

On the main Ubuntu "taskbar", choose System -> Preferences -> Search & Indexing. Choose the Indexing tab, then add the directories you want indexed using the Add button. Remember not to add directories like /dev or /proc, though. :-)

---

