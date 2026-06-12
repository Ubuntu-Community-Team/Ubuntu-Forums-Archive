---
title: "Gnome Panel (Taskbar)"
date: 2006-09-15
forum: Desktop Environments
---

### Post by voidvector on 2006-09-15
How do I prevent task bar from constantly resizing? Whenever I open/close an app, it would resize every other bar. It's visually annoying to me. 

Thanks in advanced.

---

### Post by Hunkadoodledoo on 2006-09-15
I am hoping to figure this out too.  I don't mind the resizing when I have a bunch of windows open, but I am not all about the various width depending on the title of the window.  If I am at a site in Firefox like this one "Gnome Panel (Taskbar) - Ubuntu Forums - Firefox", the window on the task bar is one third of the width of the entire taskbar.  If I then open a new tab that then changes the window to say only Firefox, it now is only about one tenth of the width.  I say boo to this.

---

### Post by psylence on 2006-09-16
Right-click the taskbar handle (on the left) -> Preferences -> Size

I believe setting the Minimum and Maximum to the same would do the trick.

---

### Post by Hunkadoodledoo on 2006-09-16
Well, what do you know!  That does the trick for me!  I couldn't find that in the documentation.  Did I just not look hard enough or is it hidden?  Thanks!

Edit: Wait.  I spoke too soon.  I am looking to be able to tell the window list not to change size of the window bars depending on the window title.  Is that possible?  Here is an example:

Say that the window list size is 800 pixels.  When one window is open, the window bar on the taskbar is 200 pixels wide.  That continues until the window bars fill the window list max size.  That would be four open windows.  The whole time that 1-4 windows are open, the window bars stay at 200 pixels each.  Then as you add windows, the window bar size is decreased by 200 - (Max Window List Size/Number of open windows).  So, with five open windows, each window bar would be 160 pixels. Six windows would be 133 pixels.  Seven, 114 pixels.  Etc.

Is there a way to tell the panel to begin this behavior?  Thanks!

---

### Post by tweedledee on 2006-12-29
> **voidvector said:**
> How do I prevent task bar from constantly resizing? Whenever I open/close an app, it would resize every other bar. It's visually annoying to me. 

Thanks in advanced.

This may be too late a response to useful to you, but here goes:

The short answer is that you cannot.  Gnome simply doesn't allow it.  You could switch to KDE, which supposedly has better behavior (although I personally find KDE a mess), or XFCE (which I like, but it's not as mature as Gnome so some features are missing).

There is a solution, however.  You can install xfce-panel, which is the panel from XFCE.  If you then run xfce4-panel (first time you can run it manually, but for constant use you can add it to your startup list), you will get the XFCE panel to appear (probably overlapping with the gnome panels initially).  In my setup, I run a gnome panel next to an XFCE panel, where the Gnome panel has most of my items, the XFCE panel just has my tasklist and a couple of other items.  This does require a little effort to configure, but actually provides a great deal of flexibility (because XFCE and Gnome provide somewhat different panel applets).  It's not perfect, because you can't get the two different types of panels to recognize each other (e.g., to stack or merge together), but it works for me.

---

