---
title: "Broken GTK icons"
date: 2011-05-16
forum: Desktop Environments
---

### Post by arloth on 2011-05-16
I recently upgraded to 11.04 from 10.10, and suddenly the majority of my icons are showing up as entirely blank, or white boxes with Xs in them.  I've attached a screenshot so that you can see what's going on.

Upon uploading the screenshot it seems that Geeqie is also unable to view jpegs.  It seems that most image support has suddenly been lost.. :-(

Has anybody seen this or knows what is going on?

---

### Post by gsmanners on 2011-05-16
Have you tried changing the Icons in Settings / Appearance?

---

### Post by arloth on 2011-05-17
> **gsmanners said:**
> Have you tried changing the Icons in Settings / Appearance?

Yes.  Changing the icons doesn't seem to change anything. I've also attached a screenshot of Geeqie being unable to display any jpegs.  

I've also noticed that if i run Synaptic - all of the installation status icons are missing, and I get lots of messages like "Warning, failed to load: package-availableUnrecognized image file format"

---

### Post by gsmanners on 2011-05-17
Upgrading is a really rough path in Ubuntu, at times. How about this?

```
sudo gtk-update-icon-cache -q /usr/share/icons/hicolor
```

or

```
sudo apt-get install hicolor-icon-theme
```

or maybe

```
rm -r ~/.local/share/icons/hicolor
``` <-- be careful with this one

---

### Post by arloth on 2011-05-19
Yeah, after some hunting I did try to remove/reinstall the icon themes, but with geeqie's trouble with images as well I figured it was some other image library that wasn't quite proper making it unable to render.

I snagged my home folder and re-installed.  There are some other issues now, but they're fairly minor compared to images/icons not working.  I didn't want to spend any more time trying to figure out exactly what went wrong.

---

