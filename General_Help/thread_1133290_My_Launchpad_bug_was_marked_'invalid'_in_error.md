---
title: "My Launchpad bug was marked 'invalid' in error"
date: 2009-04-22
forum: General Help
---

### Post by bsmith1051 on 2009-04-22
I tried to submit a bug report,
[https://bugs.launchpad.net/bugs/362050](https://bugs.launchpad.net/bugs/362050)
but it was marked 'invalid' by someone who obviously thinks it's cosmetic.  How do I dispute his evaluation?

Obviously, it's not anything critical but it's something that a lot of people have complained about since it's Not Working As Expected, and I suggested what seemed like a simple solution.
__________

Quick Summary of bug:
If you delete files on an external drive, e.g. USB flash, then the OS (Gnome?) creates a 'hidden' .Trash folder to track the files.  People complained about this and the partial solution was to prompt users to Empty Trash when unmounting the drive.  But the .Trash folder is still there and is NOT HIDDEN on Windows.  So why not just delete it, too, when you Empty Trash?  Seems obvious to me...

---

### Post by Vadi on 2009-04-22
I think you misunderstood. Empty Trash means emptying the trash on your own computer, no?

And it's not hidden on Windows because Windows doesn't respect the dot (dot in Linux means hidden). Nothing we can do about that :(

---

### Post by orlox on 2009-04-22
> I think you misunderstood. Empty Trash means emptying the trash on your own computer, no?

Actually, i think he means that when you unmount a removable USB media where you deleted files, it asks if it has to delete the trash in it (it creates a .trashsomething folder to store the trash of the media). The problem is that it leaves the .trashsomething folder

---

### Post by bsmith1051 on 2009-04-23
> **orlox said:**
> The problem is that it leaves the .trashsomething folder
Yes, exactly.

---

### Post by Vadi on 2009-04-23
Well, I set it to new again with a new explanation, lets see how it goes.

(anyone can change its status, btw)

---

### Post by bsmith1051 on 2009-04-23
Thanks!  I didn't realize that about the status.  Now, it sounds like it would be time better spent trying to convince the Gnome developers to fix this?

---

### Post by Vadi on 2009-04-24
Yeah, so it ought to be reported in the gnome bugzilla: [http://bugzilla.gnome.org/simple-bug-guide.cgi](http://bugzilla.gnome.org/simple-bug-guide.cgi)

---

