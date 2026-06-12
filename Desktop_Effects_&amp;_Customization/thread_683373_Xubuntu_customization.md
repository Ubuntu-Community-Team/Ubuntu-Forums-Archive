---
title: "Xubuntu customization?"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by jesusfreak107 on 2008-01-30
I run Xubuntu 7.10 Gutsy Gibbon.  How do you manually add visual themes and icon packages to it? I got them direct from xfce-look.org, in tar.gz format

---

### Post by PurposeOfReason on 2008-01-30
Extract them and then move the to either ~/.themes or ~/.icons depending on what it is.

---

### Post by jesusfreak107 on 2008-01-30
> **PurposeOfReason said:**
> Extract them and then move the to either ~/.themes or ~/.icons depending on what it is.
Where? I do not have a .themes or a .icons file in my File System folder, or my user ("Nerd") folder. where else would it be?

---

### Post by PurposeOfReason on 2008-01-30
If it's not there, then you've never changed the theme? Do a 

mkdir ~/.icons
mkdir ~/.themes

and they will be there.

---

### Post by jesusfreak107 on 2008-01-31
I have changed the theme before, to one of the preinstalled ones, though. I'll try that anyway...

---

### Post by jesusfreak107 on 2008-01-31
alright, I did that. Now, how do I install a package? The one I am trying to install is called AstheticGroove, and I extracted the tar.gz file. In the folder, there are two more folders.

"gtk-2.0": has a file named "gtkrc", nothing more. My computer recognizes it as a "GTK+ configuration" file.

"xfwm4":a bunch of ".xmp" files that look like thet are title bars, edges of windows, etc. there is also a text file called "themerc"
content of the file "themerc":
button_layout=|HMC
button_offset=2
title_full_width=false
title_alignment=left
title_shadow_active=false
title_shadow_inactive=false
title_horizontal_offset=2
title_vertical_offset_active=-2
title_vertical_offset_inactive=-2
button_spacing=4

Now, what do I do?

---

### Post by PurposeOfReason on 2008-01-31
Put the folder AsteticGroove into ~/.themes and keep it's subfolders (gtk and xfwm4) inside of it so it looks like this.

Home
-Username
--.themes
---asteticgroove
----gtk
----xfwm4

if that makes sense. Then you should be able to choose the theme under theme preferences.

---

### Post by jesusfreak107 on 2008-01-31
Thank you! It is now working well. I installed a different theme, too, with icons, usplash, etc. screenshot included (made possible by you)

<a href="http://s177.photobucket.com/albums/w234/jesusfreak107/?action=view&current=Screenshot.png" target="_blank"><img src="http://i177.photobucket.com/albums/w234/jesusfreak107/Screenshot.png" border="0" alt="Photobucket"></a>

---

### Post by jesusfreak107 on 2008-01-31
okay, html didn't work on that screenshot.
[IMG]http://i177.photobucket.com/albums/w234/jesusfreak107/Screenshot.png[/IMG]

---

