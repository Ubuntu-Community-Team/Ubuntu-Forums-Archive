---
title: "file manager changes directory when dragging files"
date: 2015-02-15
forum: Desktop Environments
---

### Post by JoeBeach on 2015-02-15
Hello, 

I have noticed that when I am dragging files to a directory in a file manager window in Ubuntu 14.04, the file manager will frequently switch to the new directory. I suspect there is a "hover time" setting somewhere that I can adjust to keep this from happening, but I have not been able to find any reference to it. Can anyone tell me how to either disable this feature or increase the hover time so it doesn't happen accidentally for me?

---

### Post by mc4man on 2015-02-15
There are 4 DnD on hover - 
canvas view (icon view
list view
sidebar
breadcrumbs

The canvas view one is a complete pita, there is no config on it to disable or adjust time. So the only way is to disable in the source & rebuild nautilus.
If desired can supply a patch you can apply to the nautilus source, ect.

Otherwise I have 3 nautilus ppa's for 14.04, sort of a progression of patches, all bug fixed thru current 3.10 nautilus. However the revert dnd on canvas view hover is only in the last one which has 10 patches. If curious [read carefully here]("https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1")

(- that ppa may get another patch to make the floating bar disappear on mouse-over rather than the current switch to other side behavior, really only useful in list view.
haven't decided yet..

---

### Post by JoeBeach on 2015-02-16
I nearly always use the list view, that is the one that is driving me nuts with the folder opening when I am trying to drop a file into it. Half the time I end up dropping the file into a subfolder of the one I wanted because the folder opens just before I unclick, putting the mouse over a subfolder inside the desired folder when the button releases. 

If I am reading your ppa correctly, it fixes the auto-open on hover only fir the canvas/icon view, not the list view. Do I have that right?

---

### Post by mc4man on 2015-02-17
> **JoeBeach said:**
> I nearly always use the list view, that is the one that is driving me nuts with the folder opening when I am trying to drop a file into it. Half the time I end up dropping the file into a subfolder of the one I wanted because the folder opens just before I unclick, putting the mouse over a subfolder inside the desired folder when the button releases. 

If I am reading your ppa correctly, it fixes the auto-open on hover only fir the canvas/icon view, not the list view. Do I have that right?
Correct, listview is not disabled. When this first came out I wrote 3 patches to revert 3 of the dnd/hover > open dir. but only decided to use the one on canvas view.
The sidebar & breadcrumb are actually useful, as far as list view didn't really bother me as in listview/tree the actual view doesn't alter, just expand.

You may also want to take a glance here, the middle ppa, it's to me a superior list view nautilus as compared to repo one. (I use the above one, mainly in list view with treeview enabled.
[https://launchpad.net/~mc3man/+archive/ubuntu/nauty-mods](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-mods)

---

