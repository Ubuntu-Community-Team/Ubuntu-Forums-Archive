---
title: "Multiple themes in at the same time"
date: 2006-06-06
forum: Desktop Environments
---

### Post by gynther on 2006-06-06
I have recently upgraded from Breezy to Dapper and I have also had both ubuntu-desktop, kubuntu-desktop and xubuntu-desktop installed and switched between them to test them.

Now I've gone back to Gnome and find that I'm stuck with different themes in different applications, along with different font sizes. Some applications(like firefox) change accordingly to the theme switcher, the gnome-panel doesen't. Evolution has the correct theme but the wrong font sizes.

Here are two small screens to show what I mean:

[The correct theme and font size]("http://www.gundersson.com/wp-content/uploads/christian/correct-theme.png")
[The wrong theme and font size]("http://www.gundersson.com/wp-content/uploads/christian/false-theme.png")

Notably check that the panel theme and the theme for Gimp is different and that the font in gimp and the font in firefox are different.

I have restarted both Gnome and GDM but the problem remains. I have the latest packages apt-get will provide and have also uninstalled all packages relating to xubuntu-desktop and kubuntu-desktop.

Any hints regarding this would be very helpful, my eyes are bleeding ;)

---

### Post by Nano Geek on 2006-06-06
You could try reinstalling **ubuntu-desktop** and see if that fixes it.

---

### Post by gynther on 2006-06-06
Tried that, unfortunately it didn't help. Will try to purge all the configuration files to see if that fixes it. The settings in gconf are correct, though.

---

### Post by gynther on 2006-06-06
I removed the directories .gconf, .gconfd, .gnome, .gnome2 and .gnome2_private. This resolved the problem with different themes on different applications. The problem with the fonts not resizing are still there though. Firefox resizes as it should but Gimp and Evolution(for instance) does not.

---

