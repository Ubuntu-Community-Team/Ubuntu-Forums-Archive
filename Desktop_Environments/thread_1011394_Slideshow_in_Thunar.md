---
title: "Slideshow in Thunar"
date: 2008-12-14
forum: Desktop Environments
---

### Post by Stavro on 2008-12-14
Hi All,

I'm trying out Xubuntu 8.04 and was wondering if there is any way to replicate the "Slideshow" function found in Windows 2000 and beyond in Thunar when browsing a folder full of photos?

Any help would be most appreciated.

---

### Post by john.nicholls on 2008-12-15
It depends on what program you use to view your photos. If you open one photo, you can see if that program offers a slideshow option.

John

---

### Post by mali2297 on 2008-12-15
> **Stavro said:**
> Hi All,

I'm trying out Xubuntu 8.04 and was wondering if there is any way to replicate the "Slideshow" function found in Windows 2000 and beyond in Thunar when browsing a folder full of photos?

Any help would be most appreciated.

For someone who hasn't used Windows 2000, can you describe the feature?

You might be able to replicate the feature with a custom action and, for instance, feh.

---

### Post by Stavro on 2008-12-15
Thanks for the replies. Regarding describing the function in Windows 2000, it is sort-of like a hyperlink contained within a left-hand pane when browsing folders. This picture is helpful even though it's from ME:

[http://www.winsupersite.com/images/reviews/winme_b3_26.gif](http://www.winsupersite.com/images/reviews/winme_b3_26.gif)

---

### Post by Stavro on 2008-12-15
Ahem, just a quick clarification, I'm not sure if Windows 2000 has this feature after all, but I know ME does.

---

### Post by mali2297 on 2008-12-16
My proposal is to install the image viewer **feh** (via the package manager) and create a [custom action](http://thunar.xfce.org/pwiki/documentation/custom_actions).

Set up the custom action like this:
[LIST]
[*]Name: View as slideshow
[*]Command: feh -F -D5 %d
[*]File pattern: *
[*]Appears if selection contains: Image Files
[/LIST]
Now you can right-click on an image file and select *View as slideshow*. You will see all images in the same directory as a slideshow with 5 seconds delay and in fullscreen. The image viewer has a right-click menu with options. 

If you don't want to automatically change slides, then remove **-D5** from the command above. Likewise, if you don't want fullscreen, remove the **-F** option.

---

