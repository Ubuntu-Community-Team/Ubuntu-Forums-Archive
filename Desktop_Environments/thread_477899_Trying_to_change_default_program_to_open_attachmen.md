---
title: "Trying to change default program to open attachment in Thuderbird"
date: 2007-06-18
forum: Desktop Environments
---

### Post by MindFork on 2007-06-18
I have abiword set as the "always open with" program for .doc files.  I want to switch it to open office, but I can't find any settings that control/change/remove program associations.  It seems like that once I set "always use this program" that I'm stuck for life with it. 

Anybody know how I can at least UNassociate abiword with .doc files?

Thanks,
Mind

---

### Post by evilc on 2007-06-18
Instead of l/click (open) file use right click and select open with then pick your prog, this usually changes the default opener.

---

### Post by MindFork on 2007-06-18
I tried that as well, but I only have the following choices with a right click on an attachment in tbird:

Open
Save As
Detatch
Delete
Save all
Detatch All
Delete All

---

### Post by evilc on 2007-06-18
> **MindFork said:**
> I tried that as well, but I only have the following choices with a right click on an attachment in tbird:

Open
Save As
Detatch
Delete
Save all
Detatch All
Delete All

ok use save as to a temp folder or somewhere you know then in that folder do the r/click- select, after that it should open from then on in TB in the prog you picked

---

### Post by MindFork on 2007-06-18
That made it so that .doc files are the default for the file browser, but even after restarting tbird, it is still opening them in abiword.  

Crazy, huh?  So I'm sitting here thinking "If only I could find whatever file that parameter is set in."
and duh... grep -r -l abiword * from my tbird user dir and sure enough...mimetypes.rdf -- just had to change  this:

NC:alwaysAsk="false"

to true

and I'm good to go with a choice between abiword or open office.

Thanks for the back and forth, evilc -- it got me thinking hard enough to finally figure it out.

Now...if I can only figure out how to get either one of them to NOT mangle embedded images.  That's for another thread, though...

---

### Post by evilc on 2007-06-18
No problem glad I helped clear the cobwebs:razz: TB has a habit of doing strange things sometime.

---

