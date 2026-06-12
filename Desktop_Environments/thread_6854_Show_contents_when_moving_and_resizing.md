---
title: "Show contents when moving and resizing ?"
date: 2004-12-02
forum: Desktop Environments
---

### Post by Technoferret on 2004-12-02
I am running ubunto on a old laptop and although it generally runs well I am trying to tweek it to improve performance.

One of the things I always do in both Windows and KDE is to turn off 'show window contents when moving and resizing'.
This is my first experience of using Gnome and I cannot seem to find any way to turn off this setting.
Can anybody help me or am i stuck with the default behaviour :-(

Cheers

---

### Post by Roptaty on 2004-12-02
If you are using the metacity windowmanager (default in Gnome), you might set reduced_resources to true. 

To do this you can use gconftool-2:
gconftool-2 --set /apps/metacity/general/reduced_resources --type bool true

or gconf-editor

---

### Post by Technoferret on 2004-12-02
Cheers,
Thats just what I was after.

---

### Post by keforex on 2007-11-07
Hello,

What I need is exactly the opposite, I want to show contents while resizing windows, and although my flag for the above parameter is already "false", I still see just the placeholders for the windows while resizing them. The contents are not being shown. How do I solve this problem?

Thanks!!

---

### Post by MrFurious on 2007-11-09
> **keforex said:**
> Hello,

What I need is exactly the opposite, I want to show contents while resizing windows, and although my flag for the above parameter is already "false", I still see just the placeholders for the windows while resizing them. The contents are not being shown. How do I solve this problem?

Thanks!!

I've been wondering about this as well, because showing the contents during resize was the default behavior in Feisty.  Tonight I finally figured it out.  Assuming you're using Compiz-Fusion, check out Resize Window in the CompizConfig Settings Manager.  Try changing the Default Resize Mode to Normal (mine was originally set to Rectangle).  Hope this helps.

---

### Post by keforex on 2008-03-23
Thanks! That solved the problem.

---

