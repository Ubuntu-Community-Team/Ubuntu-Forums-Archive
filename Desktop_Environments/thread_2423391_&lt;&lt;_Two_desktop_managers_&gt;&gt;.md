---
title: "&lt;&lt; Two desktop managers &gt;&gt;"
date: 2019-07-22
forum: Desktop Environments
---

### Post by icamps on 2019-07-22
Hello,

I am facing the following problem.

First, my desktop manager Nautilus (I am using Ubuntu Disco 19.04) do not show the external drives mounted icon on the desktop. Searching, I found that letting Nemo to do the work it would be possible to get the external drives icons.

So, I installed GNOME Tweaks and dconf Editor to activate/deactivate the icons on the desktop.

Now, the problem is that both of them (Nautilus and Nemo), I think, are managing everything on the desktop (even when I tried to deactivate Nautilus). I am getting a superposition of icons/files but can modify/move only one version of them.

[ATTACH=CONFIG]283657[/ATTACH][ATTACH=CONFIG]283658[/ATTACH]

Regards,

Camps

---

### Post by deadflowr on 2019-07-22
Neither have any affect on anything on the desktop on 19.04.
They removed that ability.
The icons on the desktop for Ubuntu 19.04 are handled by the gnome-shell desktop-icons extension.

---

### Post by icamps on 2019-07-22
Thanks @deadflowr,

But if I remove Nemo from loading at start, the "ghost" icons disappear. 

How do I use gnome-shell desktop-icons extension?

---

### Post by deadflowr on 2019-07-25
i guess you can run nemo to handle the desktop on 19.04.
Though to do so I had to manually start nemo-desktop.
(I have nemo installed already and it handles the desktop for unity, but never runs on gnome shell, even though it is enabled to autostart.)

The desktop icons extension is controllable through gnome tweaks (needs to be installed, if not already)
Unfortunately it's rather limited in function.
(Only has settings for home ad trash and will show all files in the Desktop folder in your home directory.
And the ability to turn it on and off seems hit or miss)

---

