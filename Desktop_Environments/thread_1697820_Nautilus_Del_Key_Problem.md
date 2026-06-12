---
title: "Nautilus Del Key Problem"
date: 2011-03-01
forum: Desktop Environments
---

### Post by gencon on 2011-03-01
Ok here's an odd one...

I like being able to use shift+del to do a backspace (del key deletes 'forwards', shift+del deletes 'backwards'), it's a feature of Windows that is not implemented as standard on Linux.

So I used xmodmap to implement this with:
xmodmap -e "keycode 119 = Delete BackSpace"
[Though the command is now in the ~/.Xmodmap file.]

Doing this stopped del working properly in Nautilus - instead of del sending a file to the wastebasket it started making del operate as a 'permanently delete this file' key.

So to fix that I used the 'dynamically change accelerators' feature (enabled in gconf-editor with: Desktop -> Gnome -> Interface -> can_change_accels). Once enabled I just hovered the mouse pointer over the Nautilus Edit Menu's 'Move to wastebasket' item and pressed del to assign the del key to 'Move to wastebasket'. Sweet!

However all this has had an unforeseen consequence. If I am renaming a file in Nautilus when I use the del key to delete characters within the file name Nautilus immediately sends the file I am trying to rename to the wastebasket. Not what I want at all. Is there any way I can stop this from happening and make del act as normal while renaming a file in Nautilus?

Many thanks.

---

### Post by oodlexaps on 2011-07-22
I have done none of the xmod mods mentioned and also have the same problem: deleting a char while renaming causes the file to be deleted.

---

### Post by gencon on 2011-07-22
> **oodlexaps said:**
> I have done none of the xmod mods mentioned and also have the same problem: deleting a char while renaming causes the file to be deleted.
I never managed to resolve the problem described above and eventually removed my Xmodmap and 'dynamically change accelerators' alterations. The advantage of having shift+del deleting 'backwards' was outweighed by the disadvantages described.

**oodlexaps** - Is this new behaviour, in other words did this not used to happen but now does?

You said that the problem "causes the file to be deleted", do you mean moved to the wastebasket or permanently deleted?

Have a look in Nautilus - highlight a file and then look in the Edit menu, is there a shortcut key associated with "Move to wastebasket"? If so it is the delete key? If so then there lies your problem (at least removing this fixed my problem, which may be the same for you)!

To remove delete as the shortcut key associated with "Move to wastebasket" in Nautilus you may first need to enable "can_change_accels", do this by:

Open gconf-editor then:
Desktop -> Gnome -> Interface -> can_change_accels (Tick this)

Then in Nautilus, highlight a file (I suggest making a copy of a file and using that instead of losing a file you want to keep if something goes wrong!), then click the Edit menu and point your mouse pointer at "Move to wastebasket" but do not click, instead hit the delete key - this will remove delete as the shortcut. Now it would probably be a good idea to go back to gconf-editor and untick "can_change_accels", so that you can not change the accelerator keys by accident (which is what I suspect you did to create the problem in the first place - but I could be wrong, it's been known before).

**NOTE IMPORTANT: **When I did the above it stopped Nautilus from deleting the file when pressing delete while renaming the file but allowed the use of the delete key in Nautilus to delete the file while not in the renaming process. Which I imagine is what you want to happen.

Hope this helps, let me know if this works or not please.

---

### Post by oodlexaps on 2011-07-22
It was "Move to Trash", and removing the delete key as an accel for it did the trick.  Thanks!  

It was new behaviour: I recently turned off Unity because it broke FFM too much at the 11.04 upgrade. I just now noticed the Nautilus problem.  But Unity's own problems could have masked it.  I'll go back and check.

I really doubt I accidentally added the accel, but it is possible since i always have it enabled.  The edit menu also has a shift+Delete accel for Delete, so I suspect they both got set by the same mechanism (update, whatever).  They may have always been set, with Nautilus previously realising that in rename mode you don't want the inaccessible edit operations to fire.  I have no idea.

---

### Post by mcduck on 2011-07-23
Del is the default shortcut for sending a file to trash, and Shift+Del is the default for deleting a file immediately. So both these shortcuts were defined before you did anything.

---

### Post by gencon on 2011-07-23
> **oodlexaps said:**
> It was "Move to Trash", and removing the delete key as an accel for it did the trick.  Thanks!  
Glad it worked.


> **mcduck said:**
> Del is the default shortcut for sending a file to  trash, and Shift+Del is the default for deleting a file immediately. So  both these shortcuts were defined before you did anything.
You are missing a subtle difference in behaviour between the default action of the delete key in Nautilus and dynamically changing the accelerator key within Nautilus and manually assigning the delete key to the Edit menu item "Move to wastebasket". In the former case you can use the delete key to delete characters when renaming a file in Nautilus, in the latter case using the delete key to delete characters when renaming a file in Nautilus will immediately delete the file, the rename will end and the file will dissappear from the Nautilus window. V. inconvenient.

---

