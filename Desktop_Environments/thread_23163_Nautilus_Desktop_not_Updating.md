---
title: "Nautilus Desktop not Updating"
date: 2005-03-31
forum: Desktop Environments
---

### Post by abock on 2005-03-31
I just installed Hoary Preview, and the only problem seems to be that nautilus will not update the desktop when changes to the directory are made outside of nautilus. Example: when I save a file from Firefox or move a file from the desktop to elsewhere through the command line, the addition/removal of the file to/from the desktop is not reflected.

The only fix seems to be to:

$ nautilus --quit

To make it redraw the entire desktop and reload nautilus.

Any clues? Is this happening to anyone else?

Thanks!
--Aaron

---

### Post by tim1 on 2005-03-31
Until the bug is fixed you can just press STRG+R to refresh the desktop. (works everywhere in nautilus)


greets, tim

---

### Post by SS2 on 2007-09-16
Two years later, and the problem still remains. Does somebody have a link to a bug or solution?

There must be something wrong in the configuration files, because that doesn't happen to every account in one system.

---

### Post by divali on 2007-09-16
I heartily agree. I've had this problem and filed the bug but, still no fix has been pointed out .
I've been without an answer to this problem for about 3 weeks (see my post under Nautilus not responding.) Lets keep this problem Alive until a fix can be found.

---

### Post by SS2 on 2007-09-16
I stumbeld around and it looks like it is a problem with gnome-vfs. I have seen that problem in three distributions (Archlinux and Debian).

Sounds a bit wierd and I haven't found the exact problem yet because that problem doesn't remain in all accounts.

My guest account works perfectly, so it could be a problem in the user directory.

---

### Post by divali on 2007-09-16
Here's the error message that I recieved:

Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

How is this done?

---

### Post by jaktar on 2008-01-15
I just came across a similar issue.  For me it's reproducible every time.

1.  On the desktop, have a file/folder selected for renaming
2.  In my tests I used firefox to save a file to the desktop or move a file from another folder to the desktop
3.  Any files added to the desktop won't update until the renaming operation is complete

The same is true for folders(e.g. move a file into a folder while renaming a file in the same folder).  However, if you have a file rename in progress in an open folder, and you save a file to the desktop, it updates immediately.  

It seems we may be seeing the product of the same problem.:confused:

---

