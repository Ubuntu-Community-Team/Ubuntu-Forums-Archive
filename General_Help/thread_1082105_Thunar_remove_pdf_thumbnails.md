---
title: "Thunar: remove pdf thumbnails"
date: 2009-02-27
forum: General Help
---

### Post by d1291 on 2009-02-27
Hello,

I'd like to remove thumbnails for PDF files only (keep them for images). I'm using xubuntu (intrepid) and thunar.

I've already tried unchecking the "enable" box in gconf-editor's /desktop/gnome/thumbnailers/application@pdf and removing the entry /usr/share/thumbnailers. I also deleted the thumbnail cache and restarted the X server. No luck - it recreates all thumbnails.

The only thing that works is deleting /usr/bin/evince-thumbnailer, but there must be a cleaner way to do this?

---

### Post by smani on 2009-02-27
I am not sure if the xfce approach is the same, for gnome, launch gconf-editor, then browse to the key /desktop/gnome/thumbnailers, and disable for the types you wish.

---

### Post by d1291 on 2009-02-28
> I've already tried unchecking the "enable" box in gconf-editor's /desktop/gnome/thumbnailers/application@pdf

Thanks for the tip - but as I said, I already tried that.

---

### Post by smani on 2009-02-28
Oh sorry, missed didn't read properly :S Unfortunately I can't help much with Xfce, the only thing I found that might work is to recompile the thunar-thumbnailer without support of those formats, but there really should be a more elegant way...

---

### Post by iShurtugal on 2010-07-19
How about taking away the execute setting for /usr/bin/evince-thumbnailer?

```

sudo chmod u=rw /usr/bin/evince-thumbnailer

```that will make it so it's only read and write, not execute for the user.  you can make it not execute for everything by using a instead of u.

---

