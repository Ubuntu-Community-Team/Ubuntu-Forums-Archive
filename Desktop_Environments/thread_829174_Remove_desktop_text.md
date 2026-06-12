---
title: "Remove desktop text?"
date: 2008-06-14
forum: Desktop Environments
---

### Post by OpVines on 2008-06-14
How do I remove my desktop text? The text looks ugly with my wallpaper and I can't find a way to remove it. I remember in Gutsy you could replace the name of the launcher with spaces and that would get rid of the text. Doesn't seem to be working this time around. Anyone have any better ideas?

---

### Post by prshah on 2008-06-14
> **OpVines said:**
> How do I remove my desktop text? The text looks ugly with my wallpaper and I can't find a way to remove it. I remember in Gutsy you could replace the name of the launcher with spaces and that would get rid of the text. Doesn't seem to be working this time around. Anyone have any better ideas?

Well you can get rid of everything on the desktop (text, icons) with this: Press Alt+F2, type gconf-editor, enter, navigate to Apps/Nautilus/Preferences and uncheck show_desktop.

---

### Post by OpVines on 2008-06-14
I like the icons, I just need a way of removing the text. Can I remove/hide the text while keeping the icons somehow?

---

### Post by OpVines on 2008-06-14
Bump?

---

### Post by urukrama on 2008-06-14
Select the icon, press F2 to rename the file, and then hit the space-bar once, so that the folder/file/launcher is now named " "). You will have an icon without text.

---

### Post by OpVines on 2008-06-14
That doesn't work in Hardy, it'll just revert to the name it was before.

---

### Post by p_quarles on 2008-06-14
One way to accomplish this would be to remove the Gnome icons completely and replace them with a desktop icon application such as idesk. It will take a few minutes of looking at the manual page, but this will allow you to set up icons exactly the way you want them, and it is easy to turn off text and tooltips.

---

### Post by prshah on 2008-06-15
> **OpVines said:**
> I like the icons, I just need a way of removing the text. Can I remove/hide the text while keeping the icons somehow?

Open System-Preferences-Appearance-Fonts-Desktop Font-Set the size to 0 (or 1 if not allowed)... that does it.

---

### Post by urukrama on 2008-06-15
> **OpVines said:**
> That doesn't work in Hardy, it'll just revert to the name it was before.

I just tried it in Hardy, with the Gnome from the Hardy repositories. It works fine here.

---

