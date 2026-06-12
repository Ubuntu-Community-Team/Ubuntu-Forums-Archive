---
title: "Problem deleting Read-Only movies/documents"
date: 2009-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tanya_814 on 2009-08-08
Hi,

A while ago, I copy/pasted a few movies and a document from a CD to my desktop. I then noticed that they had a "Read-Only" symbol attached to the folder icon. Now, when I try to delete them, it says that they cannot be moved to trash--specifically, it says "Permission Denied." 

Does anyone know how I can delete these things? 
(If you can help me, I'd appreciate it if you use easy computer language; I'm not very computer literate. Thank you!)

---

### Post by ugm6hr on 2009-08-09
The best way is to change the permissions first, then delete as normal.

Press Alt+F2:
Enter in box: **gksudo nautilus**

Select all (Ctrl-Left click) files to delete.
Right-click on one of the already selected files.
There should be a tab called permissions or something like that.
Change all entries to Read and Write.
Click Apply to all.

Close this window now.

Then try deleting again.

The reason for this, is that the CD will have had read-only files, and copying them maintained those "permissions".

You could just delete them from the gksudo nautilus window directly, but this would have the effect of putting them in the "root" users Trash, not your own.

Some further reading: [http://www.psychocats.net/ubuntucat/rootlauncher/](http://www.psychocats.net/ubuntucat/rootlauncher/)

---

### Post by tanya_814 on 2009-08-10
It worked!!!
Thank you SO much!!!
:D :D :D!!!

---

### Post by tanya_814 on 2009-08-10
hmm...i havnt been on these forums in a while. 
do they still have the 'thank you' and 'problem solved' options? :)

---

### Post by running_rabbit07 on 2009-08-10
Nope, I think the staff can add the [solved] to the thread title though.

---

### Post by tanya_814 on 2009-08-10
ah, ok. Thank you!

---

