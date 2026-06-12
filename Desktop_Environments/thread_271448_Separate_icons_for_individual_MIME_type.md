---
title: "Separate icons for individual MIME type"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Van_Gogh on 2006-10-04
Hi,

I program in Python, and to visually distinguish my Python files from my other text files, I'd like to have a seperate icon for the Python MIME type(text/x-python). Is that do-able?

The right-click-> properties -> Select custom icon seems to change the icon for ALL text files, which is not what I want.

Any help would be greatly appreciated.

---

### Post by Van_Gogh on 2006-10-05
Anyone?

---

### Post by CatKiller on 2006-10-05
> **Van_Gogh said:**
> Hi,

I program in Python, and to visually distinguish my Python files from my other text files, I'd like to have a seperate icon for the Python MIME type(text/x-python). Is that do-able?

Certainly, and some themes, like Amaranth, do this. I haven't tried this, but in principle it should work:

Find the directory for the icons for the theme that you are using. This might be in /usr/share/icons, or it might be ~/.icons, or it could conceivably be somewhere else entirely. Then you need to guess at which directory holds the mimetype icons. If the icons are SVG, then this is easy: they'll be in scalable/mimetypes. Otherwise, it might be 48x48, or somewhere else, depending on the theme.

Once you've found the correct folder for your particular theme, you'll need to put your new icon in there and call it gnome-mime-text-x-python. Hopefully it'll work straight away.

---

### Post by lazork on 2006-11-09
> **CatKiller said:**
> Once you've found the correct folder for your particular theme, you'll need to put your new icon in there and call it gnome-mime-text-x-python. Hopefully it'll work straight away.

While I think this is how it worked on Ubuntu 6.06 (or gnome 2.14), it doesn't seem to work anymore since I upgraded to the newer version.
Now all script files share the same icon regardless of the file extension and the same goes for any other file type (video, audio, text...).
Why has this happened?
Is there a way to fix it?

---

