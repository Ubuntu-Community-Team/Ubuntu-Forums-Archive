---
title: "GNOME Start-up problem"
date: 2006-01-09
forum: General Help
---

### Post by gingermark on 2006-01-09
Hey,

Been using Kubuntu since Hoary (used GNOME in Warty) but thought I'd give the brown stuff another go, so installed the ubuntu-desktop metapackage (actually, that's a lie, I didn't install evolution. But everything else that metapackage points to). I even switched to GDM, just for a change.

Tried logging in to GNOME and once the startup screen disappears, the two bars that make up the menu. taskbar, clock etc etc appear, without any markings whatsoever, then disappear, then appear, then disappear, and I have to ctrl-alt-backspace out of the loop. The background is just one colour of brown, no ubuntu wallpaper.

Some things that might be of interest (or might not be):

I deleted all the gnome folders in my Home directory, because I wanted to see what the Breezy Ubuntu desktop was like without it being affected by previous settings. Sure enough, there are new gnome folders in Home now.

I'm using the majority of the repositories listed in the [source-o-matic](http://www.ubuntulinux.nl/source-o-matic), including many of the unofficial ones.

I had been having problems in Xfce, where the panel disappeared. But I don't use Xfce, so I didn't worry. But I know Xfce and GNOME are linked in someway, so maybe that has something to do with it?


Let me know if you need any more info, any help would be appreciated.

---

### Post by BathroomNinja on 2006-01-09
I could be wrong, but I think Ubuntu's Gnome depends on some evolution packages.  Perhaps use apt again, but this time don't ignore any packages.

---

### Post by gingermark on 2006-01-09
Installed ubuntu-desktop in order to catch the missing packages, but still have the same problem.

I also tried to remove xfce, as I have no need for it, and had been having the aforementioned problems. Removed nearly all the pakages associated with xfce, except for a couple that affected rox-filer (and by extension affected mezzo, ubuntu-lite, and fvwm), but that didn't improve matters.

Any other ideas?

---

### Post by BathroomNinja on 2006-01-11
Honestly, no.  Other than the old 'backup, reinstall'.  But I'm sure there is a better way.  I wish I could see terminal output to see what's hanging it up, but I don't know how to get that when starting X.

---

