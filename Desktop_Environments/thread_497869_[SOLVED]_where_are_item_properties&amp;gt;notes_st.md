---
title: "[SOLVED] where are item properties&amp;gt;notes stored?"
date: 2007-07-10
forum: Desktop Environments
---

### Post by logos34 on 2007-07-10
> 6.6.17.1.&#8195;To Add a Note Using the Properties Dialog

To add a note
to a file or folder, perform the following steps:

   1.Select the file or folder to which you want to add a note. 
                
   2.Choose File &#8594; Properties. The properties window for the item is displayed.
                
   3.Click on the Notes tab. In the Notes tabbed section, type the note.
                
   4.Click Close to close the properties
      dialog. A note emblem is added to the file or folder.
                

To delete a note, delete the note text from the Notes tabbed section.

WHERE are these added notes and emblems STORED???

I just copied over all my saved docs to a new feisty install but the notes and emblems have disappeared :-(

I have looked in home (+ .hidden) and /root.  It would seem they should be somewhere in /home/user.

---

### Post by David Castelow on 2007-07-12
They are in files called something like ./.nautilus/metafiles/file:*

---

### Post by logos34 on 2007-07-13
> **David Castelow said:**
> They are in files called something like ./.nautilus/metafiles/file:*

Thanks!  That's exactly where they were...I would swear I checked that folder but either didn't go into the metafile subdirectory or all those strangely-named .xml files ('file:%2F%2F%2Fhome%2F...') threw me.

Now my notes and emblems are back.  :)

---

### Post by logos34 on 2007-09-27
oops, forgot to mark this thread as solved...

---

