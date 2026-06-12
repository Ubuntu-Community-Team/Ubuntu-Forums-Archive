---
title: "Help installing themes"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Dave Burbank on 2006-07-30
Hi All,

I am having difficulty installing new themes that I have downdoaded from the net.  In gnome, if I open System> Preferences> Themes the theme manager comes up and I am able to select from any of the pre-installed themes.  My problem is when I try to install new ones.  If I drag-and-drop the package (.tar.gz) into the Theme Preference window or click 'Install Theme...' I get and error that says 'The file format is invalid'.  Any thoughts? Thanks.

---

### Post by ardchoille on 2006-07-30
The installer in the theme manager is crappy, IMHO. It returns errors when it shouldn't and it won't allow you to install multi-theme tarballs. The best practice is to unpack a gtk theme into ~/.themes for a user theme or unpack it into /usr/share/themes to make the theme available system-wide.

I stopped using the theme manager's installer a long time ago.

---

### Post by Dave Burbank on 2006-07-30
If I try to unpack it to /usr/share/themes I get a error saying that I don't have permission.  How do I use the sudo command in the gui, or better yet, how do I unpack files to a destination using the terminal.  Once I've unpacked it, how do I select it as my primary theme? Can I use the theme manager to select it? Thanks.

---

### Post by chickengirl on 2006-07-30
> **Dave Burbank said:**
> If I try to unpack it to /usr/share/themes I get a error saying that I don't have permission.  How do I use the sudo command in the gui, or better yet, how do I unpack files to a destination using the terminal.  Once I've unpacked it, how do I select it as my primary theme? Can I use the theme manager to select it? Thanks.
After you've unpacked the theme into either /usr/share/themes or ~/.themes, it will show up in the theme manager like normal.

---

### Post by Dave Burbank on 2006-07-30
Ok I've gotten the theme unpacked to /usr/share/themes but it still doesn't show up in the theme manager.

All of the theme folders in /usr/share/themes have either a text file and/or a xml file, while the folder (theme) I add has .png .jpg and a .xml files, could this be part of the problem.

Also the sub-folders for the pre-installed themes are named 'gtk-2.0' while the theme I am trying to install has 'GDM' in its name.  Could this be a compatibility issue?

---

### Post by Dave Burbank on 2006-07-30
This shows just how much of a n00b I am, I was trying to install GDM themes when I should have been installing GTK themes.  Trial by error,  I'm learnig slowly!

---

