---
title: "Desktop Shortcuts KDE 3.5"
date: 2006-01-10
forum: General Help
---

### Post by jadugarr on 2006-01-10
Is there a way to remove the shortcut overlay (that little icon) from desktop shortcuts that you create by dragging folders from konqueror to the desktop?

---

### Post by aysiu on 2006-01-10
Can you post a screenshot of this? I'm not sure I know what you're talking about.

---

### Post by wanger123 on 2006-01-10
He means the little arrow  in the bottom left hand corner of a file icon (same as winblows) that is due to saying 'link here'. Instead of 'link here' you can just say 'copy here' unless you are worried about duplication (if it is too large). 
I could not find out how to turn the arrow icon off either.
wanger

---

### Post by jadugarr on 2006-02-04
Yeah, I gave up trying to figure this out.  You can manually add links to the desktop and they won't have the link arrow on them.

---

### Post by ace2005 on 2006-02-04
Well just change the images in the KDE Icon theme:

In the konqueror address bar type:

> locate:overlay

to search for overlay

and then you should see a folder like /home/--your username--/.kde/share/icons/--Theme Name--

Go into there and you should see the overlay files, edit them in an editor of your choice and make the whole thing transparent, done!

Although there has to be an easier way to do this, like some command in some config file

---

