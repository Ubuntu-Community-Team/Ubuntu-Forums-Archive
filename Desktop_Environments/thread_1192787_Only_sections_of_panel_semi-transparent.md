---
title: "Only sections of panel semi-transparent"
date: 2009-06-20
forum: Desktop Environments
---

### Post by BlueCanary9999 on 2009-06-20
Hai.  I'm trying to make the panel somewhat transparent, but only sections of it work.  The main menu, notification area, date, and volume controls stay opaque according to the theme.  Maybe screenshots would be more descriptive....

As you can see from the attachments, the global menu doesn't even work fully, and the transparency works in sections.  How do I make the entire panel semi-transparent?

---

### Post by BlueCanary9999 on 2009-06-20
Wait, nevermind.  I found a way around it.  See here:
[http://ubuntuforums.org/showthread.php?t=952098&highlight=blur+transparent+windows](http://ubuntuforums.org/showthread.php?t=952098&highlight=blur+transparent+windows)

EDIT:
Wait, no, I take that back.  It blurs windows related to the panel, too.

---

### Post by BlueCanary9999 on 2009-06-21
Bump....

---

### Post by spoketire on 2009-06-24
I have just the thing for you. Get a png image that has an alpha channel, so it will be semi-transparent, and set it as the background image for the panel through the right click menu. This should solve all your problems. The whole panel will be semi-transparent, but none of the panel-related windows will be. Another benefit of this method is that the icons and text will remain opaque while the background around them is not, so it's still easy to read everything.

Here's a png I use, but it's not gray like your panel is (and it might not be wide enough for your screen). It comes with the Dust theme. You can try it out to get the idea. Or you can make your own if you know how. It's pretty easy in the GIMP.

---

### Post by BlueCanary9999 on 2009-06-27
Sorry for the late reply.

If I set a background for the panel, only those sections that were able to turn semitransparent in the pictures in my first post would get the background.  The rest will remain the opaque default according to the theme.

---

### Post by mcduck on 2009-06-28
> **BlueCanary9999 said:**
> Sorry for the late reply.

If I set a background for the panel, only those sections that were able to turn semitransparent in the pictures in my first post would get the background.  The rest will remain the opaque default according to the theme.

Your GTK theme is now defining a background for those parts of the panel, and that overrides what ever you do in the panel's configuration.

You'll need to either use some other GTK theme, or edit the current one and remove the parts that define background for panel components.

---

### Post by spoketire on 2009-06-29
The png I have was actually from the Dust theme, which is pretty nice. So if you want to try that one, the background should go over the whole bar. A lot of themes I've tried allow me to set the background for the whole bar, so just look around a bit.

---

### Post by BlueCanary9999 on 2009-07-09
Ahh, I see.  It's in the "Controls" tab in the GTK theme Customize part.  Damn. I rather like New Wave.  How would I "edit the current one and remove the parts that define background for panel components"?

And sorry for the late reply again.  I very much appreciate your help.

---

### Post by mcduck on 2009-07-10
> **BlueCanary9999 said:**
> Ahh, I see.  It's in the "Controls" tab in the GTK theme Customize part.  Damn. I rather like New Wave.  How would I "edit the current one and remove the parts that define background for panel components"?

And sorry for the late reply again.  I very much appreciate your help.

Find the directory where you installed the theme (most likely osmewhere in ~/.themes), open any gtkrc files and remove/comment out any sections that define images for panels.

Quite many themes actually have a separate panel.rc (or something like that) file which includes all panel-related parts of the theme. If your theme does that, simply renaming this file should work.

---

