---
title: "Wine: How can I access files in hidden folders?"
date: 2008-12-23
forum: General Help
---

### Post by SteveDee on 2008-12-23
When running applications under Wine (e.g. Notepad) how can I open files within hidden folders?
The Open dialog does not show {.name} type folders. 

Is there a config setting or a trick for this?

---

### Post by Zorael on 2008-12-23
In the Wine configuration window (winecfg), under the Drives tab, there's a checkbox for "Show dot files". That sounds like it could be it?

---

### Post by SteveDee on 2008-12-23
> **Zorael said:**
> In the Wine configuration window (winecfg), under the Drives tab, there's a checkbox for "Show dot files". That sounds like it could be it?

Yeah, you'd think so, but it doesn't seem to make any difference.

I think the problem displaying .name files in Windows apps is that the Open dialog is looking for *.* files, not .* files. So if I create a file in gedit and call it .me, when I open Notepad under Wine I cant see it. But if I type .me into the file name field of the Open dialog it opens OK.

This is OK if you know the name of the file and you can access the folder. But what I want to do is navigate to a hidden folder using WinMerge, then compare hidden files. So its getting to the hidden folder that is the main problem.

Maybe I should just find a good Linux alternative to WinMerge!

---

### Post by ajgreeny on 2008-12-23
In the open file dialog, if you choose *All files* in the *File type* drop-down box, all the hidden files show up, or at least they do in Notepad.  What I can't get it to do is see hidden folders, so it will not do quite what you want.

Just out of interest, why on earth do you need to use Notepad when you've got gedit or any other linux text editor available?

---

### Post by SteveDee on 2008-12-23
> **ajgreeny said:**
> In the open file dialog, if you choose *All files* in the *File type* drop-down box, all the hidden files show up, or at least they do in Notepad.  What I can't get it to do is see hidden folders, so it will not do quite what you want.

Just out of interest, why on earth do you need to use Notepad when you've got gedit or any other linux text editor available?

I've even tried the good old Windows trick of rebooting the OS, but I still can't see the .me text file in Notepads Open dialog.

As you may now have gathered, I was only using Notepad as an example. It was WinMerge that I was really interested in.

---

### Post by mc4man on 2008-12-23
Try it this way, (with show dot files checked in winecfg  and also in nautilos for good measure

When you browse in the open file box choose 'my computer' and pick Home (H: ) as your entry into home.

Should show hidden files

---

### Post by SteveDee on 2008-12-23
> **mc4man said:**
> Try it this way, (with show dot files checked in winecfg  and also in nautilos for good measure

When you browse in the open file box choose 'my computer' and pick Home (H: ) as your entry into home.

Should show hidden files

Yeah that basically works with Notepad & WinMerge:-

 -select "All Files" in Open dialog
 -drill down to "My Computer"
 -select drive (in my case "Z:" )
 -navigate back up to required folder

Both hidden files & folders are displayed, and this did not need "Show Hidden Files" in Nautilus.

Many thanks.

---

