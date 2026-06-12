---
title: "Desktop Icons Overlap"
date: 2009-05-08
forum: General Help
---

### Post by Altay_H on 2009-05-08
One thing that has always irritated me about Ubuntu's desktop is the way the icons' names are seemingly unrestricted. The filenames flood the desktop in such a way that text and icons overlap in a chaotic mess.

Some screenshots should demonstrate what I'm trying to say. In the first screenshot I have four folders with excessively long names placed as close together as I normally place my icons. The tangled mess makes the filenames mostly illegible. The second screenshot demonstrates how far apart I must place the icons in order to ensure there is no overlap.

Does this not bother anyone else? Has anyone come up with a good solution? Why can't Ubuntu manage desktop icons more like Xubuntu? Is there some simple setting I'm overlooking?

It would all be so much nicer if I could just restrict file names to 2 lines before they're shortened with an ellipsis (...) and allow files to lock to the grid horizontally in as small increments as they do vertically.

Finally, I've also had problems with files or folders occupying the exact same space on the desktop. This is especially true when I plug in a USB drive and the icon appears on the desktop. The third screenshot demonstrates this problem. Is there any way to prevent files/folders from occupying the exact same space on the Desktop?

Thanks for any help!

---

### Post by Egi_Power on 2009-05-08
Hi!

I don't know how to solve it.

I just wanted to say, that I'm really happy that I found your thread, because it was bothering me as well.
For example I have some icon on the desktop, then I load a CD or DVD in the drive and its icon appears exactly on the other icon. It is really annoying.

Btw, I'm curious if there is a cure for this odd behavior.

Take it easy.

Egi_Power

---

### Post by Altay_H on 2009-05-08
This thread looks like it has a solution for the horizontal overlap problem: [http://ubuntuforums.org/showthread.php?t=1033592](http://ubuntuforums.org/showthread.php?t=1033592)

It suggests running gconf-editor, then:
apps > nautilus > icon-view > default_use_tigher_layout

I'll give it a try when I'm back on my Ubuntu machine.


EDIT:
There's also already a bug report:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/40872](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/40872)

Unfortunately the bug has been declined for every release of Ubuntu since 6.06. I suppose there's always hope that GNOME 3.0 will finally fix this issue.

---

### Post by Dougie187 on 2009-05-08
> **Altay_H said:**
> This thread looks like it has a solution for the horizontal overlap problem: [http://ubuntuforums.org/showthread.php?t=1033592](http://ubuntuforums.org/showthread.php?t=1033592)

It suggests running gconf-editor, then:
apps > nautilus > icon-view > default_use_tigher_layout

I'll give it a try when I'm back on my Ubuntu machine.

Just so you know, I just tested it in 9.04 and it doesn't fix the icons from overlapping all that setting does is restrict the box that the text can be in below the icon to the icon's width. It doesn't prevent icons or text from overlapping each other.

---

