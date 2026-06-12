---
title: "Icons aren't applying properly!"
date: 2009-09-21
forum: Desktop Environments
---

### Post by SPARTAN-118 on 2009-09-21
Hi, whenever I try to apply a new icon theme, (user-created, anyway - theme packages, such as Oxygen, work fine) only certain icons get applied; the only ones I know that are acting as they are *supposed* to are the tarball icons (.tar.gz) and Computer. There might be more, but those are the only I know of. All others appear as a dull, grey, flat, and ugly folder icon. However, my Firefox icon changed, and my Places screenlet has little folders that go with the supposed theme. Is my resolution too big or something?

This happens with most icon packages, please help!

SPARTAN-118

---

### Post by gadolinio on 2009-09-22
Mmmm maybe those themes have some cions missing; when that happens, default ones are used. I woul compare the content on the folders inside the costom icon theme with the content inside an "official" one; if you see that for example you theme doesn't have a folder called "mimetypes" inside "scalable", that could be the reason. Whenever i make a custom icon theme, i start from a default one such as Human-gnome-tangerine-etc, and then replace the ones i want to look different. It takes some time, as there are different PNG files for each icon for each size (16x16, 32x32, 48x48, scalable, etc).
Hope you find this useful. If you don't, maybe you could send me a zip file with one of those icon themes and i or another user tell you what happens.

---

### Post by SPARTAN-118 on 2009-09-22
> **gadolinio said:**
> Mmmm maybe those themes have some cions missing; when that happens, default ones are used. I woul compare the content on the folders inside the costom icon theme with the content inside an "official" one; if you see that for example you theme doesn't have a folder called "mimetypes" inside "scalable", that could be the reason. Whenever i make a custom icon theme, i start from a default one such as Human-gnome-tangerine-etc, and then replace the ones i want to look different. It takes some time, as there are different PNG files for each icon for each size (16x16, 32x32, 48x48, scalable, etc).
Hope you find this useful. If you don't, maybe you could send me a zip file with one of those icon themes and i or another user tell you what happens.

Well, there isn't a folder called "scalable," just "extras."

Should I rename it and create a folder in it called mimetypes?

---

### Post by gadolinio on 2009-09-23
Try to follow the structure of an existing icon theme, to get to know how this works. For example,go to /usr/share/icons/gnome. You'll see that inside the gnome folder you have the folders: 8x8, 16x16, 22x22, 24x24, 32x32, 48x48, scalable. Inside each of them (well, not all of them, but generally speaking) you have folders like "places", "mimetypes", "apps", etc. Look inside, pick the miniatures view (don't know how to call it in english; i mean the option to view little pictures corresponding to each file, instead of the image_icon). Make your icon theme follow that structure, and the system will use the icons correctly. "Places" has the icons for folders, the main menu, and stuff like that. Mimetypes has the icons to represent each file type (.xls, .doc, .txt, web pages, etc). Apps has the icons that represent each program (the file manager, firefox, synaptic, etc). I haven't seen a folder called extras, so i don't know if it has any function. I can tell you that without any folder called that way, i've personalized icons in every way i wanted.
If you manage to upload the package of icons i can organize them and test the theme myself; then post it back. Or you might well copy the structure (and file names) of an existing theme.

---

### Post by SPARTAN-118 on 2009-09-23
> **gadolinio said:**
> Try to follow the structure of an existing icon theme, to get to know how this works. For example,go to /usr/share/icons/gnome. You'll see that inside the gnome folder you have the folders: 8x8, 16x16, 22x22, 24x24, 32x32, 48x48, scalable. Inside each of them (well, not all of them, but generally speaking) you have folders like "places", "mimetypes", "apps", etc. Look inside, pick the miniatures view (don't know how to call it in english; i mean the option to view little pictures corresponding to each file, instead of the image_icon). Make your icon theme follow that structure, and the system will use the icons correctly. "Places" has the icons for folders, the main menu, and stuff like that. Mimetypes has the icons to represent each file type (.xls, .doc, .txt, web pages, etc). Apps has the icons that represent each program (the file manager, firefox, synaptic, etc). I haven't seen a folder called extras, so i don't know if it has any function. I can tell you that without any folder called that way, i've personalized icons in every way i wanted.
If you manage to upload the package of icons i can organize them and test the theme myself; then post it back. Or you might well copy the structure (and file names) of an existing theme.

Well here how about I send u the package, and I'll also give u some screenies of one working icon set and the one that doesn't work.

According to the structure you send me back, I think I'll be able to fix all other broken icon packages.

Ahem... the package is too large, I'll provide a link: [here]("http://www.1-filehost.midnightirc.info/index.php?t=dl&hash=Mu17auig4JHE3Npe6vNhf3wl92qJdwuj")

As for the pictures...

---

### Post by gadolinio on 2009-09-23
Hey i can't download anything but a 200KB file that cannot be extracted. It's not 8MB as the page says at first. Can you upload it somewhere else?

---

### Post by SPARTAN-118 on 2009-09-24
> **gadolinio said:**
> Hey i can't download anything but a 200KB file that cannot be extracted. It's not 8MB as the page says at first. Can you upload it somewhere else?

Hrm... ok, that was the original file download page...

Well, anyways, I guess it was just some icon themes, since I DL'd some more from gnome-look.org and they work perfectly.

I'll try to find the gnome-look page (nouvext-vista?), but I'll have to do that later.

Thanks,
SPARTAN-118

---

