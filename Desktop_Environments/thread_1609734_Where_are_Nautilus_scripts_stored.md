---
title: "Where are Nautilus scripts stored?"
date: 2010-10-30
forum: Desktop Environments
---

### Post by Nick Payne on 2010-10-30
Where are Nautilus scripts stored? After I installed jEdit, I now have an "Open with jEdit" option on the right-click context menu, and I want to modify that to reuse the existing jEdit view rather than create a new one. However, both my ~/.gnome2/nautilus-scripts and ~/.nautilus folders are completely empty, so where are the scripts stored?

---

### Post by kerry_s on 2010-10-30
look in synaptic, click on jedit, click properties, then installed files.

---

### Post by Nick Payne on 2010-11-02
Thanks, the file I needed to change was /usr/share/jedit/jedit.sh. For some reason (why couldn't they just leave things alone), the jedit.sh that gets installed when installing jEdit 4.3.2 from the 10.10 repository is not the same as the jedit.sh that gets installed if I download the jedit 4.3.2 deb from the jedit web site and install from that. The one from the repo gives the annoying behaviour - not very user-friendly.

---

