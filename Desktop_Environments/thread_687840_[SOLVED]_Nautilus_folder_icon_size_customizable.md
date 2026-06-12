---
title: "[SOLVED] Nautilus folder icon size customizable?"
date: 2008-02-04
forum: Desktop Environments
---

### Post by nikosm on 2008-02-04
Dear fellow ubuntu users,

I really like Nautilus' feature of being able to choose any image as a folder icon. I noticed that if the image I choose is too big, it is being scaled down automatically, to some extend. So, obviously, there is an upper limit on the size of the image that can serve as an icon to a folder. Can I adjust the maximum image dimension, and how? And can I adjust it so that the maximum size is different for each folder?

Unrelated to that, I was wondering if there is a way to hinder Nautilus from ignoring leading underscores when sorting alphabetically (I mean, I want this alphabetic ordering: "_b a b c" but I am getting this: "a _b b c"). I saw this question in an old unanswered post, maybe we became wiser in the meantime...? This is not crucial, but it would be nice to know if I can deactivate it (after all it is a feature somebody had to build, not something that happens by mistake).

Thans a lot,
Nikos

---

### Post by loboc on 2008-02-04
In the right click context menu there is a stretch icon option that is stored on a icon by icon basis. Somewhere in the preferences for nautilus there is a universial icon size setting but my Gnome box is at work and cant remember exactly where it is.  If you use svg icons then they wont get blurry and ugly as you stretch them.

---

### Post by Tenken on 2008-02-04
The universal setting loboc mentioned sets the global maximum dimensions for all icons (sorry, not just folders).

To change it, open gconf (Alt + F2, then type "gconf-editor") the setting is under:
apps->nautilus->icon view->thumbnail_size

---

### Post by nikosm on 2008-02-05
Hello loboc and Tenken,

Thank you for pointing out the thumbnail-size option. I have a folder with pdf's and I would like to have those thumbnails big, but the rest normal size. But I would already be very happy if there was a possibility to set the thumbnail size for every filetype independently. Do you know if this is possible?
I discovered another option related to thumbnails in the configuration editor:
schemas/desktop/gnome/thumbnailers/

I don't know what a schema is or what this options do.

Thanks again,
Nikos

---

