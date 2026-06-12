---
title: "[SOLVED] Fix Nautilus thumbnail size?"
date: 2008-01-12
forum: Desktop Environments
---

### Post by geoken on 2008-01-12
Is there any way to make nautilus display it's thumnails previews more like thunar?

In thunar the thumbnails are scaled to fit within a container that's equal to the size of the icons. This makes the folder contents appear in a perfect grid, which in turn makes it much easier to quickly locate files. 

Conversely, nautilus resizes the thumbnails to some arbitrary number that is seemingly unrelated to the icon size. This effectively makes the row spacing different from row to row.

Is there anyway to make nautilus' behavior more like thunar's?

---

### Post by geoken on 2008-01-12
I took a few screencaps to illustrate what I mean.

Here's Nautilus;

[IMG]http://i5.photobucket.com/albums/y169/geoken/naut.jpg[/IMG]



Now heres Thunar displaying the exact same folder;

[IMG]http://i5.photobucket.com/albums/y169/geoken/thun.jpg[/IMG]




Just to show that the icons are actually the same size, here they are side by side;

[IMG]http://i5.photobucket.com/albums/y169/geoken/sBs.jpg[/IMG]



What I'm trying to find out is if nautilus has any option that will allow you to keep the thunmbnail previews within certain dimensions so they can look tidy like thunar does.

---

### Post by catach on 2008-01-12
Hmmm. In the configuration editor, 
apps>nautilus>icon_view
Set thumbnail size to something small like 50 (default should be 96). 

In my limited testing that does away with the worst of the effect.

---

### Post by geoken on 2008-01-12
Awesome.

That did exactly what I needed.

Thanks catach.

---

