---
title: "Lost my screensaver"
date: 2009-06-24
forum: Desktop Environments
---

### Post by John Jason Jordan on 2009-06-24
Recently I had a disaster with rdiff-backup that made the backup to a mount point instead of the external media, thus filling my disk 100%. After recovering lots of things were messed up in Gnome and Nautilus.

Although it took hours of research I have restored all settings to the way they were, except I cannot find my screensaver. I was using Xmatrix, but it is no longer listed when I go to System > Preferences > Screensaver. In fact, most of the screensavers listed there do not work. (They used to.) Glmatrix and Matrixview are listed, but they do nothing now.

I can't understand what happened. How could the above error have uninstalled applications? Or are the screensavers applications? How do I get my screensaver back?

---

### Post by philcamlin on 2009-06-24
why do you need a screensaver 

save power turn your screen off :) or lock it so it turns off after 20 min

---

### Post by John Jason Jordan on 2009-06-24
It just occurred to me that the solution may be simple.

Another thing that happened when the disk went to 100% was that I lost my Nautilus bookmarks. These are contained in /home/<username>/.gtk-bookmarks. After figuring that out I looked and it turns out that filling the disk to 100% caused something to create a new .gtk-bookmarks file of 0 bytes, and renamed the old one .gtk-bookmarks~. I just did a quick file rename and my bookmarks were back.

So the screensaver options must be in a file somewhere as well. If it was renamed as *~ and a new one created in its place, all I have to do is find the original file and rename it back to what it was. 

That's just a theory. But if anyone knows where Gnome saves settings like that, please let me know.

---

