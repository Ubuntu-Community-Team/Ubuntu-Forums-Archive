---
title: "Video thumbnails won't load in Lucid Lynx"
date: 2010-05-02
forum: Desktop Environments
---

### Post by Kenanbiel on 2010-05-02
Hello there,

I'm currently using Lucid Lynx and my video thumbnails won't load. I already modified my preferences that thumbnails would always load, and set that files smaller 4GB will load. Only the generic video thumbnails load. I already tried deleting the files in ~/.thumbnails/fail/gnome-thumbnail-factory/ but still problem exists.

---

### Post by aphirst on 2010-05-02
I've encountered the same problem. I've bypassed it for now by using ffmpegthumbnailer. It took about 15 minutes of tedious adding of keys to gconf, but it 'works'.

The Totem thumbnailer was pretty much perfect for me in 9.10; what on Earth happened? :P

---

### Post by Kenanbiel on 2010-05-03
I think it is a codec problem. I just did this: ***sudo apt-get  install ubuntu-restricted-extras*** and it's already loading.

---

