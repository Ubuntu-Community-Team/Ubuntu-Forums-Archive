---
title: "Thumbs look blurry on desktop"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by tseo on 2007-12-06
I have images on the desktop and when I resize the thumbs so they look bigger and better they actually look very blurry. Is there a way for the thumbs to be rendered more sharply cause I don't see sense in having them bigger sized if they look so bad.
Thanks

---

### Post by judolars on 2007-12-06
Icons appear blurry when resized if the icon theme you use doesn't provide SVG (scalable vector graphics) versions of the icons. "Human", the default icon theme in Ubuntu, only provides icons for a few applications, such as OpenOffice.org.(Try adding a launcher for OOo Writer to your desktop and scale it, and you will see what I mean.)

The solution is therefore to find an icon theme which has the icons you need in SVG format. (Suggestions for good themes, anyone?)

---

### Post by tseo on 2007-12-09
I understand what you mean but what I actually need is for the thumbs of .jpg files to look nice when scaled but apparently this won't be possible...

---

### Post by mcduck on 2007-12-09
I'm not sure if this changes the resolution of the generated thumbnails or just the size they are dispalyed, but if you open Configuration Editor (run 'gconf-editor') and browse to apps/nautilus/icon_view there's option for thumbnail size..

---

### Post by tseo on 2007-12-09
Thanks for the advice but this changes only the size of the thumb and doesn't affect the resolution.

---

### Post by tseo on 2007-12-12
I was just wondering - If I change the desktop/window manager is there a chance I'll get some result?

---

### Post by phenest on 2007-12-12
I have several hundred JPEG's and some give high resolution thumbnails as I enlarge them, whereas most go blurry. I think it has something to do with the image itself.

---

### Post by zekopeko on 2007-12-12
i'm afraid that this is because gnome generates thumbs in one resolution so when you stretch it looks blurred. i think i saw on a blog of some gnome dev that he fixed this in SVN of gnome so you should get that in the next ubuntu version

---

### Post by phenest on 2007-12-12
I worked out how to get clear large thumbnails. But they have to be lower quality. I made a copy of a picture and used Gimp to reduce the quality (to about 10%) of the JPEG when I saved it. The result was a nice clear thumbnail.

So it seems that high quality pictures give blurry thumbnails whilst low quality pictures give clear thumbnails.

This is obviously a workaround.


> **zekopeko said:**
> i'm afraid that this is because gnome generates thumbs in one resolution so when you stretch it looks blurred. i think i saw on a blog of some gnome dev that he fixed this in SVN of gnome so you should get that in the next ubuntu version

If this Gnome dev has fixed it, does that mean just updating one library? Can that be done?

---

### Post by tseo on 2007-12-16
Thanks very much:)

---

