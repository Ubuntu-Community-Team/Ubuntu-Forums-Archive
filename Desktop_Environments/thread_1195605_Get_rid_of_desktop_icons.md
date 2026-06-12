---
title: "Get rid of desktop icons"
date: 2009-06-24
forum: Desktop Environments
---

### Post by John Jason Jordan on 2009-06-24
I used to have a clean screen - no icons at all. Recently I had a disaster with rdiff-backup that made the backup to a mount point instead of the external media, thus filling my disk 100%. After recovering lots of things were messed up in Gnome and Nautilus.

I have restored everything except that the icons are back on my desktop and I can't figure out how to get rid of them. I'm pretty sure I did it in gconf-editor, but it was several years ago and I can't find the key. Or maybe it was a setting somewhere else.

Can someone tell me how to get rid of the icons on my desktop?

---

### Post by ~sHyLoCk~ on 2009-06-24
gconf-editor -> apps->nautilus->desktop
Uncheck the icons

---

### Post by John Jason Jordan on 2009-06-24
> **~sHyLoCk~ said:**
> gconf-editor -> apps->nautilus->desktop
Uncheck the icons

Thanks, but the icons were already unchecked.

I did "killall nautilus" and the icons disappeared. But the minute I launched Nautilus again they were back.

I forgot to say I have Jaunty x86_64, Gnome 2.26.1.

Any more suggestions?

---

### Post by measekite on 2009-06-24
> **John Jason Jordan said:**
> Thanks, but the icons were already unchecked.

I did "killall nautilus" and the icons disappeared. But the minute I launched Nautilus again they were back.

I forgot to say I have Jaunty x86_64, Gnome 2.26.1.

Any more suggestions?

Goto nautilus in gconf-editor and uncheck Show Desktop.  Then nothing in the desktop folder will be visible but it will still be available from the file system /home/user/desktop.

This works because I just did it on 2 different computers and I also did it in both Ubuntu and Fedora.

Let us know if you get it.

---

### Post by John Jason Jordan on 2009-06-24
> **measekite said:**
> Goto nautilus in gconf-editor and uncheck Show Desktop.  Then nothing in the desktop folder will be visible but it will still be available from the file system /home/user/desktop.

This works because I just did it on 2 different computers and I also did it in both Ubuntu and Fedora.

Let us know if you get it.

Thanks for the reply. I just found it by myself at about the same moment you posted your reply.

To clarify you left out a couple folders. In gconf-editor (type gconf-editor in the command line) you go to apps > nautilus > preferences and then uncheck show_desktop.

Thanks to all for the pointers. And next time it breaks and I need to reconfigure it I'll hopefully remember the answer is here in the forums. :)

---

