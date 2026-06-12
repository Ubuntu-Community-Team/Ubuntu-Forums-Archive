---
title: "iconsets won't install"
date: 2006-08-01
forum: Desktop Environments
---

### Post by hollowhead on 2006-08-01
I've had this problem for a while and I'm sure others do.  I've downloaded some great iconsets which when I try to install (by drag and drop) in the themes dialog won't install and give an "invalid file format" error message.  Is there any way round this? About 30% install fine.

---

### Post by Ares Drake on 2006-08-01
Well, either your download is broken, or - more likely - there are different icon sets in that archive file. Just unzip / untar it and install the set you wish

---

### Post by hollowhead on 2006-08-01
Ta.  I'll try the latter.  NH

---

### Post by ardchoille on 2006-08-01
The gnome theme manager installer isn't very good at all because it sometimes gives errors where it shouldn't and it can't handle multi-theme tarballs. I suggest that people unpack theme tarballs into:

unpack gtk themes into ~/.themes

unpack metacity themes into ~/.themes

unpack icon themes into ~/.icons

If you want to make the themes system-wide, unpack gtk and metacity themes into /usr/share/themes and unpack icon themes into /usr/share/icons.

---

