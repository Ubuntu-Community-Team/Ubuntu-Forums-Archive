---
title: "Can Caja be made aDefault FileBrowser on Ubuntu FlashbackDesktop"
date: 2018-04-21
forum: Desktop Environments
---

### Post by ubix on 2018-04-21
Hi everyone,

I'd like to set **Caja** as default *File Editor* on Ubuntu 16.04 *Clasic Gnome Flashback Desktop*. I know this would work in *Ubuntu MATE Desktop*, but I do not want to install, nor run *Ubuntu MATE Desktop*.

So far I made **Caja** my *File Manager*, however, *Ubuntu GNOME Flashback Desktop* is still using Nautilus to manage folder icons on the Desktop, _which broke regular file handling on desktop, like copying and pasting files to and from desktop folders_ or between Caja and Nautilus file browsers. I would like to disable Nautilus, as the File Manager all together, short of un-installing it. Occasionally, I'd still like to be able to have access to Nautilus by choosing a file browser of my choice, for instance, when I right-click on a folder icon, via "**Open With**" menu option on desktop.

Also there are times when I'd like to swap Nautilus and Caja as desktop File browsers, by either modifying **~/.local/share/applications/mimeapps.list**, or by running **exo-preferred-applications** command  from terminal, or perhaps doing something else I haven't discovered and/or tried yet.

Does anybody have any suggestions? [unnecessary content removed]

---

### Post by kerry_s on 2018-04-21
> Does anybody have any suggestions? [unnecessary content removed]


ssh, it's true. careful there watching.

---

### Post by kerry_s on 2018-04-21
okay, i got to know why?

there the exact same file manager, caja is a nautilus fork to work on mate desktop. so why bother? i can understand if it was a different file manager, maybe a lighter 1, but why the same file manager under a different name?

---

