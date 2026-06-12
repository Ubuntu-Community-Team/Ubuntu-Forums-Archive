---
title: "Easily replace all icons in Ubuntu with custom ones"
date: 2010-01-17
forum: Desktop Environments
---

### Post by dmillerw on 2010-01-17
So I found this icon pack online, called Token Dark ([http://brsev.deviantart.com/art/Token-128429570]("http://brsev.deviantart.com/art/Token-128429570")) and I'd love to use it in Ubuntu, but its just a ton of PNG's.

Is there any easy way to replace the icons in Ubuntu with those, or do I have to manually replace every one in the .icons folder.

---

### Post by dmillerw on 2010-01-17
Anyone?

---

### Post by phredbull on 2010-02-10
You're supposed to be able to install custom icons either by drag and dropping the icon pack onto System>Preferences>Appearance Preferences, or by using the Install... button on the aforementioned window.

That being said, I installed the icons pack, "Nerdy Lines", but not all of the icons have changed, (folders, Nautilus menu, and Gnome menu icons are still showing as default Gnome icons. I guess I should make my own topic for this...)

Hope this helps!

---

### Post by dannyboytward on 2010-02-18
I've been fiddling with icons a lot lately, and I have a few suggestions.

1) If you want to use a set of png's as an icon theme, make sure there is a file called index.theme in the directory containing all the subfolders and icons.  If there isn't (I see that the token-dark theme doesn't have one), you can make one as a text file (it's probably easier to just copy and modify an existing one) and there is a reasonably good tutorial here: [http://live.gnome.org/GnomeArt/Tutorials/IconThemes](http://live.gnome.org/GnomeArt/Tutorials/IconThemes). 

2) If some of the icons don't change when you add a new theme, it might be because they are named incorrectly.  Here are some "proper" names:
folder-documents.png
folder-download.png
folder-music.png
folder-pictures.png
folder-publicshare.png
folder-templates.png
folder-videos.png

I have downloaded icon sets where these files are not named correctly, and had to change them to the above (for example "downloads" instead of "download", "images" instead of "pictures")

3) If some icons don't change, it might just be because they are not included in the set.  In this case, you can still go into the index.theme file and find a line that looks something like this:
Inherits=gnome,hicolor
You can change it to include icons you like better when one is missing from the set.  For example I changed mine to:
Inherits=Humanity-Dark,Humanity,gnome,hicolor

Hopefully this is some help.

---

