---
title: "Customizing icons on gnome desktop? (trash / mounted partitions)"
date: 2007-03-17
forum: Desktop Environments
---

### Post by khughitt on 2007-03-17
Hiya,

Anyone know how to customize the icons displayed on the desktop? In windows, there is a place in the display settings where you can chose to display or not to display "my computer", "recycle bin", etc.. is there any similar feature in gnome? I would like to have an icon for the trash can displayed on my desktop, and also to remove the icons for my mounted drives / dvd-rom.

any suggestions?

Thanks!
Keith

---

### Post by ardchoille42 on 2007-03-17
> **pwnedd said:**
> Hiya,

Anyone know how to customize the icons displayed on the desktop? In windows, there is a place in the display settings where you can chose to display or not to display "my computer", "recycle bin", etc.. is there any similar feature in gnome? I would like to have an icon for the trash can displayed on my desktop, and also to remove the icons for my mounted drives / dvd-rom.

any suggestions?

Thanks!
Keith

Open gconf-editor, Applications -> System Tools -> Configuration Editor, and go to /apps/nautilus/desktop and check the boxes next to the icons you want on your dekstop. You can even choose the names that appear under the icons.

---

### Post by neon777 on 2007-04-15
Thanks!

---

