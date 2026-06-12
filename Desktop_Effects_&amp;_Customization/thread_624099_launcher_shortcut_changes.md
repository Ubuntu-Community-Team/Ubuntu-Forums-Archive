---
title: "launcher shortcut changes?"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by valkyr47 on 2007-11-26
If i select evolution email under the program list and select "add launcher to desktop" it makes the shortcut, but the icon is mini-sized and i dont like it. Is there any way to replace icons for programs in ubuntu?

i know this sounds like a nitpick but im very particular about my computer and i want the icon to be full sized if possible, or just outright replace it with a better email icon

thanks!

---

### Post by macaholic on 2007-11-26
The easiest way is to just right-click on the launcher and go to properties and change it by clicking on the icon. Now this only changes it for that particular launcher. The harder, but more thorough way (will change all instances of that icon), is to go to a launcher, click on the icon again, note the location of the icon. For example the loaction of the firefox icon is /usr/share/pixmaps/firefox.png.
Now, all you do is put the new icon you want on your desktop. name it so that it is the same as the icon you are replacing, and do
```
sudo cp ~/Desktop/<icon_name>/path/to/file
```
For firefox it would look something like this:
```
sudo cp ~/Desktop/firefox.png /usr/share/pixmaps/firefox.png
```
for evolution it would look something like
```
sudo cp ~/Desktop/evoltion.png /usr/share/icons/hicolor/scalable/apps/evolution.svg 
```
Things to note:
This will change if you have a different icon theme set other then GNOME, also depending on the name of the icon you are trying to replace it with, the file extension will change. Generally [svgs]("http://en.wikipedia.org/wiki/Svg") are the best choice for icons, but hi-res pngs work well also.

---

