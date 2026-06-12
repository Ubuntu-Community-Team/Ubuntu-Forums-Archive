---
title: "Problem with maximum Gnome Terminal window size"
date: 2011-09-14
forum: Desktop Environments
---

### Post by lotuseclat79 on 2011-09-14
Normally, I work from a Live CD environment in the Gnome environment (Maverick).

The 80x24 default minimized size of a Terminal window is fine.  However, when I maximize the Terminal window, it resizes to (238x57) which does not allow it to be resized at the corners.

I do not know if this is a result of the font pixel size (default) or some other cause, and I have a Samsung 21.5 inch monitor.

What I do know from resizing a minimum sized Terminal window and resizing it at the corners is that the correct size of a maximized Terminal window is (237x57) which allows access to the corner resizing graphic symbol.  But, this result is only for the minimum size while the maximum size is still (238x57) which cuts off the left hand column of listed text files when the Terminal window is maximized with the maximize button.

What is the correct gnome-terminal command to specify both the minimum and the maximum sizes for a gnome Terminal window to correct this sizing problem?

-- Tom

---

### Post by grayraven on 2011-09-14
Hey Tom,

I am not sure if this is exactly what you are looking for, but you can set the default dimensions on launch. Have you tried launching it using the --geometry flag. You can see more information about it in the man page, or google "gnome-terminal geometry". I believe there are some other properties that you can set through the profile. If I find something I think will help I will post it.

Cheers,

James

---

