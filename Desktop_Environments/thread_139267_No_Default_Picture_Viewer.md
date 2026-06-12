---
title: "No Default Picture Viewer"
date: 2006-03-03
forum: Desktop Environments
---

### Post by crford on 2006-03-03
So, I'm a long time Gnome user who has decided to give KDE a look and can't seem to figure something out.  I installed Ubuntu 5.10 and then the Kubuntu metapackage, which installed a ton of other packages.  I rebooted and went into KDE, which has come a long way since I saw it BTW, and I can't do anything with .jpg, .png or .gif files.  There is no thumbnail for them, and if I try to open them in Konqueror, it asks what app to open them with.  I can open them in any of my Gnome apps, or KView.  But I can't set them as a wallpaper or anything on the system level.  Any ideas where to look would be graciously accepted.

---

### Post by GeneralZod on 2006-03-03
The lack of thumbnails is odd; go into Thumbnail View mode, click View, Preview  and check the things you want to preview (specifically, Images, but try out some of the others, too! :)).  I think there's a slightly quicker and more convenient means of doing this, but I can't remember what it is :)

To set wallpaper, you can either right-click on the desktop, Configure Desktop->Background, or drag an image from Konqueror onto the desktop and choose Set as Wallpaper.

---

### Post by crford on 2006-03-03
Preview mode is on.  It is generating previews for everything else, but not image  files. When I try to change the wallpaper, I can't select any .jpg, .png, or .gif files.  As a matter of fact, they don't even show up when I browse to a folder that has the images in it.  It's like the system doesn't have the graphics libraries installed or something....

---

### Post by GeneralZod on 2006-03-03
Something's definitely gone wrong there :)

Try installing kdemultimedia and libmagick - you can find them both in the repositories.

---

### Post by crford on 2006-03-03
Already have both of those installed.  Any other ideas?

---

### Post by GeneralZod on 2006-03-04
[QUOTE=crford]Already have both of those installed.  Any other ideas?[/QUOTE]

Dang - no, I'm all out :/

You could try upgrading to KDE 3.5.1, I guess - there are a few guides here on the forums.  It's pretty disruptive, though.

---

### Post by crford on 2006-03-04
Already have that too.  I guess I'll reinstall and try adding Gnome apps and libs as necessary and see how that works.

---

