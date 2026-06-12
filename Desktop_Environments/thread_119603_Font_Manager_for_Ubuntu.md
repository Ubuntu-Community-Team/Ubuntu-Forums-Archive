---
title: "Font Manager for Ubuntu"
date: 2006-01-19
forum: Desktop Environments
---

### Post by tonyrebelgreen on 2006-01-19
How do you put new fonts - ttf fonts - so they are usable in Ubuntu? I can't find a font installer or manager amongst the available package lists I have. Can anybody recommend such a bit of software which is available to download?

---

### Post by dcstar on 2006-01-19
[QUOTE=tonyrebelgreen]How do you put new fonts - ttf fonts - so they are usable in Ubuntu? I can't find a font installer or manager amongst the available package lists I have. Can anybody recommend such a bit of software which is available to download?[/QUOTE]
Open your Nautilus file browser (as Root user), and put this in the Location:

fonts:///

Search for the HOWTO on how to install extra fonts for more details.

---

### Post by Michael Steinberg on 2006-01-19
Alternatively--to add fonts for yourself and not for the entire system--put them in a directory (folder) in Home. Then open System -> Preferences -> Fonts. Click on Details, and (finally!) click on Go to font folder.

Drag your new fonts into this window.

Nothing will happen--the fonts won't show up in the fonts window and they won't be moved from the folder in your Home directory. When you log out of Gnome & back in again, though, or after you restart, you'll find that you've added the new fonts.

---

### Post by Madpilot on 2006-01-20
[https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto) has more details - I use a /.fonts file, that way I know exactly where the things actually are.

---

