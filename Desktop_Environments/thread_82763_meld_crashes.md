---
title: "meld crashes"
date: 2005-10-27
forum: Desktop Environments
---

### Post by pgabriel on 2005-10-27
Meld is a visual diff tool.
As explained better in this [thread]("http://www.ubuntuforums.org/showthread.php?t=74305") meld crashes when trying to open a file using the Open File dialog. 
The problem was not solved in Breezy and I can replicate it each time.

Is there a workaround for this problem?

---

### Post by Spie on 2005-10-27
Hi,

I just installed Meld because Gnome lacks a good tool to synchronize directories (KDE: Krusader) and I was hoping that Meld could meet my demands. But I have the same problem.

---

### Post by dpm on 2005-10-27
Yep, just to confirm, I have got exactly the same problem, also running Breezy 5.10. 

I have found a workaround by dragging the files directly to the textboxes on the "Choose Files" dialog. It is the only way to get it working for me.

I haven't done any research to see whether this is a known issue or not, I'm going to do this later if I've got time.

Cheers.

---

### Post by Spie on 2005-10-27
After some googling I found that it is a GTK/pyGTK bug and if you install from CVS the problem should be gone. But, and I quote: "For those who are unable to patch (for whatever reason), a patch-free workaround is to not use GtkFileSel to select your directory. Simply type the path in the text field instead."

Now it works like a charm and it was the program I was looking for.

Hope this will help you!

---

### Post by pgabriel on 2005-10-27
Is there a chance to fix the PyGTK file selection dialog in the current release (Breezy) or in backports?

---

### Post by pgabriel on 2005-10-28
Went one step further and created a bugzilla entry for this one here: [http://bugzilla.ubuntu.com/show_bug.cgi?id=18594](http://bugzilla.ubuntu.com/show_bug.cgi?id=18594)

---

### Post by ow50 on 2005-10-29
This seems to be fixed in meld 1.1.1, which is available in the dapper repository.

---

### Post by pgabriel on 2005-10-31
Tested the latest release meld 1.1.1 and it works because they use the file selection dialog from Gnome.
Also the source code highlighting works, this feature does not work correctly with the version shiped in Breezy.

---

