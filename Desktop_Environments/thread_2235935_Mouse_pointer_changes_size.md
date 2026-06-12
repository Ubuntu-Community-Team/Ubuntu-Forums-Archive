---
title: "Mouse pointer changes size"
date: 2014-07-23
forum: Desktop Environments
---

### Post by Hesediel on 2014-07-23
Hi i have lubuntu 14.04
) 
i installed a theme for the mouse pointer: Comix cursor [http://gnome-look.org/content/show.php/ComixCursors?content=32627](http://gnome-look.org/content/show.php/ComixCursors?content=32627)

Here the problem: i was looking for change the size and i found that giving that command in the terminal

```
leafpad ~/.Xresources

```

and putting:  Xcursor.size: 50   i can change the size, ok it works. But i see that the cursor changes the size when i open a windows.  In the desktop the size is bigger, that i wrote in the file, if i open firefox, ore something else it reduces its size. Its lower in the window and bigger in the panel and in the status bar of the window, why? some one knows how can i set and get to stay one size?

---

### Post by Dennis N on 2014-07-23
How did you install the cursor theme? In Lubuntu 14.04, I suggest you use this process to install your new cursor properly:

[http://ubuntuforums.org/showthread.php?t=2234783&p=13075327#post13075327](http://ubuntuforums.org/showthread.php?t=2234783&p=13075327#post13075327)

In the commands, replace Pulse-Glass with the name of your cursor theme.

Edit: Looked at Comix Cursors. To do the steps in the installation you would first need to add a cursor.theme file to the cursor's folder. If you installed ComixCursors-Orange, it would look like:

```
[Icon Theme]
Inherits=ComixCursors-Orange
```

Make it with the text editor, then save it inside the cursor's folder.

---

