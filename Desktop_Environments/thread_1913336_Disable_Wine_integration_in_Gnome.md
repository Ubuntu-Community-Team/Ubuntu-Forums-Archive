---
title: "Disable Wine integration in Gnome"
date: 2012-01-22
forum: Desktop Environments
---

### Post by CardexDave on 2012-01-22
Hello everyone!

I just updated my Ubuntu and noticed that the nice Wine icon defined by me icon theme is now replaced by the real icon from the exe file, which does not suit with my icon theme at all, not mentioning the size issue.
Screenshot: [_click here_]("http://dl.dropbox.com/u/188481/wow_icon_screenshot_for_wine_forums.png").
The custom icon I made for the launcher and which suits my icon theme is the second icon in the dash (it's World of Warcraft if you wondered), the original exe icon is at the bottom.
On this screenshot the size issue does not look really critical, but it is clearly more aggressive on the alt-tab pop-up window of gnome shell. I was unable to take a screenshot of the said pop-up window because for some reason it never appears on it.
I already opened a thread on the wine forum (I was writing it at the time of the screenshot) as I don't really know if it is wine related or more a Ubuntu problem.

I already removed gnome-exe-thumbnailer, but the icon is still there.
I already deleted the .thumbnails folder as well.
It's been two days since I have been searching for a cached icon or something like that that would have been burried somewhere in the filesystem after its extraction the first time I launched my wine application, but I couldn't find any...

Please help me, I want wine applications to display with the wine icon defined by the icon theme, not the real exe icons which are not suited to be displayed in size greater than 32x32 or 48x48 and does not suit my icon theme...

Thank you,

Dave

PS: English is not my native language, so I apologize for my spelling/grammar...
PS2: I'm not sure to be in the right section of the forum, feel free to move this thread if needed, sorry...

---

### Post by Frogs Hair on 2012-01-22
I have made a few custom icons for specific applications . In some cases the icons replaced are in file system usr/share/pixmaps .

In this location administrator permission is needed  to remove or replace the image file . Simply removing the icon may not work if it is part of the program GUI .  

If the program is updated the icons will return to the program provided icons if they are stored in pixmaps .

---

### Post by CardexDave on 2012-01-22
That was one of the first places I looked at but it wasn't there... =/

---

### Post by sanderd17 on 2012-01-22
I have the same problem with some Java apps as Josm or geogebra.

I have search a bit for those apps, and the only possibility I found was to recompile the Java source.

Let me know if you find something better.

---

### Post by CardexDave on 2012-01-22
Yes Java apps display their own icons, that's true, but Windows exe apps dis not in the previous version of Ubuntu.
I had no problem like this one before I installed the new Ubuntu Oneiric...

---

### Post by JustinR on 2012-01-22
edit: nevermind

---

### Post by CardexDave on 2012-01-29
Bump!

I don't understand, I don't have this issue on a similar setup using the current Linux Mint, which is supposed to be based on Ubuntu, right?
It seems unrelated to Wine (as wine forumers had suggested trying older versions) as I am running wine version 1.3.37 on the Linux Mint desktop.

So anybody has a clue to how wine integration and icon extraction works in current Ubuntu?

---

