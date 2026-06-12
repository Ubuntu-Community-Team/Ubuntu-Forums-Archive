---
title: "[SOLVED] How do I change file type icons?"
date: 2008-09-09
forum: Desktop Environments
---

### Post by dangermouse28 on 2008-09-09
How do I change file type (mime type) icons in Gnome?

Many thanks!!

---

### Post by Diabolis on 2008-09-09
If you are using custom icons, e.x. downloaded from gnome-look, go to your **.icons** folder and replace the icons that it already has with your own. The **.icons** folder is in your home folder. As you can see it has a dot in the beginning of its name, this means that it is a hidden folder. In nautilus press **<Ctrl>h** to see all the hidden files.

If you are using one of the sets of icons that come pre-installed with Ubuntu, you'll have to overwrite them here: **/usr/share/icons**

Instead of overwriting a icon I recommend you to modify a copy, so you won't lose the original set.

---

### Post by dangermouse28 on 2008-09-10
I've tried that but with no success. 
I have several icon sets I've downloaded from gnome-look and they're installed in .icons. 
I wanted to change the icon for .doc files. I found all the icons in the mimetypes folder which had msword in the name and changed them to the new icon.
Restarted Gnome, logged back in but no change.
I don't understand how the icons aren't changing even though I've changed the files in .icons - it's like they're being cached somewhere else...

Can anybody help???

---

### Post by billgoldberg on 2008-09-10
> **dangermouse28 said:**
> I've tried that but with no success. 
I have several icon sets I've downloaded from gnome-look and they're installed in .icons. 
I wanted to change the icon for .doc files. I found all the icons in the mimetypes folder which had msword in the name and changed them to the new icon.
Restarted Gnome, logged back in but no change.
I don't understand how the icons aren't changing even though I've changed the files in .icons - it's like they're being cached somewhere else...

Can anybody help???

Try a reboot then.

Are you sure you changed the right theme and have that exact theme selected in appearance -> icons?

---

### Post by dangermouse28 on 2008-09-10
Yep - tried that too, no success.

Definitely right theme, right iconset.

It's a fresh Hardy install using the "alternative" CD - cos I wanted to encrypt my hard drive.
I've also installed the Emerald Theme manager. Can't think what else might be different from standard...

---

### Post by Languid Heap on 2008-09-10
I was pulling my hair out over this one too.

I can't remember where I read it, but the solution for me was as follows (where THEME is the name of your icon theme):

1. Delete the file ~/.icons/THEME/icon-theme.cache
2. from the console: ```
sudo gtk-update-icon-cache ~/.icons/THEME/
```

And that did the trick for me. 

HTH

---

### Post by dangermouse28 on 2008-09-11
Fantastic! - thanks very much, that did the trick.

I'm going to post a short How-to on how to do this so others don't have to waste a week of life trying to do something which is actually very simple!

[http://ubuntuforums.org/showthread.php?t=916847](http://ubuntuforums.org/showthread.php?t=916847)

---

