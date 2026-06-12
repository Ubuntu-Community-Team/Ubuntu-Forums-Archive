---
title: "automount .iso when double-clicked?"
date: 2006-03-27
forum: Desktop Environments
---

### Post by aaulick on 2006-03-27
I can easily mount a .iso from the command line, but I want to set things up so that my 5-year-old kid can do it by double-clicking the .iso, and then ideally unmount them in Gnome in the same way CDs can be unmounted with the "eject" context menu option from the desktop icon in Gnome.

Is there a utility to do this that works well with Ubuntu?

Ideally the mount-point would be predictable, so that whichever ISO was mounted first could be associated with a drive-letter as a CD-ROM in wine without extra work.  

I'm tired of looking for and replacing scratched kids' titles all the time.

---

### Post by dragonfyre13 on 2006-03-27
It's not a double click, but check out the script on my site. Stick it in the gnome scripts folder.

[http://www.dragonfyre13.com/TimWiki/MountIsoFiles](http://www.dragonfyre13.com/TimWiki/MountIsoFiles)

---

### Post by aaulick on 2006-03-30
Thanks!  That helps.

---

### Post by drummer on 2006-03-31
To use that when double-clicking, tou could put that script in /usr/share/bin or somewhere else in your PATH and associate it with the ISO mime type. Am I right? I'll try it when I get home.

---

### Post by dragonfyre13 on 2006-04-06
I'm not sure, since it uses some command line args for this. It should, but don't bet the farm.

---

### Post by louis_nichols on 2006-04-08
another way is krusader. it's an app I love and opens iso's on-the-spot, like it treats most archives. also, if you want to REALLY mount stuff, you can also use dragonfyre13's script and associate iso's with it.

---

### Post by e^e on 2006-04-08
nvm

---

