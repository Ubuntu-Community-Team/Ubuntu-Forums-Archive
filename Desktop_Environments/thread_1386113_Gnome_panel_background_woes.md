---
title: "Gnome panel background woes"
date: 2010-01-20
forum: Desktop Environments
---

### Post by El Zoido on 2010-01-20
Hello!

I guess many of you encountered this problem:
When a gnome-theme applies a pic (e.g. to create a gradient) I cannot make panel sizes > 24 pixels look good, as I will have the pic at the top 24 pixels and the default color below, or the pic again in case the size is equal to or greater than any natural multiple of 24.

It's even worse for vertical panels, which are affected much more by this tiling issue.

So, does anybody know of some workaround (except from not using background pics)?

---

### Post by digitalchemystery on 2010-01-20
You'll have to use an image which tiles gracefully (or an image the width of your panel).

The default behavior of gnome-panel appears to be tiling in x and and y when an image smaller than the panel is used. If an image is meant to fit a specific height (or, basically, doesn't look good when 'looping around' by being tiled), you'll see the problems that you do.

The solution in your case is to either use an image which tiles gracefully (i.e. a pattern which can be repeated) or to use an image of the correct size.

---

### Post by digitalchemystery on 2010-01-20
Sorry, I missed that you were using vertical panels...

it's the same story though.

---

### Post by El Zoido on 2010-01-20
Well, I'm using both actually.
Guess I could try to manually set an background image.
Not sure though if that will work in combination with the gradient/image set by the theme.
The most user-friendly way would be if gnome-panel would simply stretch the image...

---

### Post by mcduck on 2010-01-20
Gnome-panel does support scaling the images, and even allows selecting between scaling while maintaining images proportions or simply stretching the image to fit the panel. And rotating the images to fit vertical panels.

To change the scaling/rotating options you need to open gconf-editor, browse to *apps/panel/toplevels/<name of your panel>/background* and enable 'rotate' and 'stretch' (or you can use 'fit' instead of 'stretch' depending on what you need).

Be aware that these settings don't apply to images set by GTK themes, only for backgrounds you have set in the panel's preferences. So if you have any background image set to panel itself or any panel widgets in your GTK theme you need to edit the theme to remove the image, and then apply the image as panel background from the panel's preferences. Otherwise you end with the background being correctly scaled in panel itself but all the panel applets using the background *without* scaling it.

---

### Post by El Zoido on 2010-01-20
Thanks a lot!
While this is not exactly what I was hoping for it will still help, I think.

---

