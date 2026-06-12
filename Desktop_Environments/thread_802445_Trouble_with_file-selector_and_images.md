---
title: "Trouble with file-selector and images"
date: 2008-05-21
forum: Desktop Environments
---

### Post by MaX on 2008-05-21
I have a problem with my image folder... In some folders there are alot of images but they refuse to show up in the file-selector and thus cannot be added as backgrounds.
Drag-and-drop into the background image view doesn't work either.
I have read-write right's and all that stuff in the folders. Nothing different from the other images (as far as I can tell).

Help!
[IMG]http://www.midgard.liu.se/~l06marwo/WhereAreMyImagesX2.png[/IMG]

---

### Post by bmac on 2008-05-21
It appears your attempting to use jpg's for desktop background. You need to convert the jpg's to png's then add them to your background. You can use gthumb to "save as" png by selecting it in the "Image type" box. Don't forget to give it a name in the top box...


Hope this helps...

---

### Post by MaX on 2008-05-21
> **bmac said:**
> It appears your attempting to use jpg's for desktop background. You need to convert the jpg's to png's then add them to your background. You can use gthumb to "save as" png by selecting it in the "Image type" box. Don't forget to give it a name in the top box...


Hope this helps...

That's stupid... Gnome is perfectly capable of using JPEG's as backgrounds... Oh well I'll try that.

That didn't work.. check this out.. Ghtumb doesn't show the JPEG images... But Nautilus happily makes thumbnails...
[IMG]http://www.midgard.liu.se/~l06marwo/no-images-in-list.png[/IMG]

---

### Post by MaX on 2008-05-21
Turns out it was this bug causing it...
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/198154](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/198154)

---

### Post by bmac on 2008-05-21
gthumb shows jpeg's just fine on my system and converts them to png's with no problem. The jpegs don't show in my Appearance Preferences/Background and when I attempt to add them they don't show in the menu. I may have a problem and didn't know it... I've just been converting them to png's and everything works fine... I'll investigate why they aren't showing up in my add menu....
Glad you found the bug....

---

