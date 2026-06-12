---
title: "gnome-screenshot will not use Desktop as destination dir"
date: 2013-06-06
forum: Desktop Environments
---

### Post by gdea73 on 2013-06-06
For a while I've been having this problem with the gnome-screenshot utility: I can't save to the desktop.

When the dialog opens, the default destination directory is ~/Pictures (I wish it would remember the last used dir, but that's a separate issue).
I then click on the dropdown menu and select Desktop. After clicking on Desktop, the text changes to ".fr-20GNNv/"

If I click "Browse," the file browser puts me in ~/Desktop with ".fr-20GNNv/" in the filename bar. I can then delete .fr-20GNNv/, click open, and use the desktop.

Why is this happening?

(Also, things get weirder: if at the file browsing dialog I hit "tab," repeatedly, it gradually fills out this entire dir path: ".fr-20GNNv/install/netboot/ubuntu-installer/i386/boot-screen/")

---

### Post by gdea73 on 2013-06-06
Well strange, that folder (~/Desktop/.fr-20GNNv/.../boot-screen/) existed and had a blank something.cfg file in it. I deleted .fr-20GNNv/ and I think it's all working now.

---

