---
title: "[SOLVED] Rename desktop folder"
date: 2008-03-16
forum: Desktop Environments
---

### Post by iris-n on 2008-03-16
Hi all,

I run ubuntu in portuguese, so my desktop folder is named "Área de Trabalho", which is incredibly inconvenient to type at bash. I'd like to rename it desktop, lowercase, but if I do  that nautilus loses track of the folder, and shows my /home contents in the desktop instead. So, how can I tell it the new name? Already looked in ~/.nautilus and /etc, for configuration files, to no avail.

Thanks in advance,

Iris

---

### Post by lian1238 on 2008-03-16
You can create a link of the Área de Trabalho folder and rename the link to desktop. :D
(To create a link, middle click and drag the Área de Trabalho folder and click Link Here)

---

### Post by iris-n on 2008-03-16
It seems that that would work, but i've already broken the path somehow, changing the name back won't work. And i don't want to create another user & all.
Also, I would find more elegant to directly edit the nautilus files, i've never found (yet) a unhackable part of linux.

---

### Post by iris-n on 2008-03-16
bump?

in ~/.nautilus/metafiles there are a bunch of xml files, that seems related to my /home, but changing them seems to have no effect whatsoever. Are they?

---

### Post by iris-n on 2008-03-16
I've found it.
At ~/.config, there's user-dirs.dirs
It stores the paths for the standard bookmarks, including the desktop one.
Was only a matter of restarting gnome to my desktop to work properly.

Hope it's of use to anyone.

---

