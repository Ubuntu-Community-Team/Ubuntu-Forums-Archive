---
title: "GVFS mounted file systems are not shown in most GTK application dialogs"
date: 2011-08-07
forum: Desktop Environments
---

### Post by r.darwish on 2011-08-07
When mounting a virtual file system using GVFS it can be easily accessed using Nautilus. However, when I use most of my GTK based applications (i.e. Firefox or VLC), the virtual file systems are not shown in the "Open file" or "Save file" dialogs.
These file systems can be still accessed from the .gvfs folder, but as I understand, this folder is ment to support command line or non-GTK applications, and my problem exists with GTK applications. Accessing these file systems through .gvfs is less comfortable and less intuitive.
Is this a bug, misconfiguration or a feature by design?

I am using Ubuntu 10.04.03 LTS

---

### Post by fulopattila122 on 2012-11-18
This problem still exists in 12.10. Additionally the ~/.gvfs/ folder has been moved to /run/user/<username>/gvfs/

You can live with it, but I'm afraid for less power users it might be a serious barrier.

---

### Post by aquarius18 on 2012-12-04
> **fulopattila122 said:**
> This problem still exists in 12.10. Additionally the ~/.gvfs/ folder has been moved to /run/user/<username>/gvfs/

You can live with it, but I'm afraid for less power users it might be a serious barrier.

Had this working on 11.10 and also in a cloned 11.10 with subsequent update to 12.04

Used info from **[this thread]("http://ubuntuforums.org/showpost.php?p=9941016&postcount=3")** to make it happen.

**BUT:  **just did a fresh install of Mint 14 (= 12.10) then installed Gigolo as per link above. The NAS mounts automatically (as it should) and I can access it via Nautilus but the GVFS does not appear in the menus of applications.

Got around this problem this way: 

1. open Nautilus
2. select GVFS mount
3. hit CTRL+D to create a Bookmark

If I now want to save something from an application or select a file from the GVFS it shows up in GTK application dialogs.

Not a nice way of doing it but it works.

---

### Post by wildmanne39 on 2012-12-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

