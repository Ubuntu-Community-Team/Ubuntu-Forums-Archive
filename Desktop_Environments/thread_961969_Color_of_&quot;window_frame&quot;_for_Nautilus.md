---
title: "Color of &quot;window frame&quot; for Nautilus"
date: 2008-10-28
forum: Desktop Environments
---

### Post by Mark_in_Hollywood on 2008-10-28
I'm such a dweeb about 'puters. I wish that the "windows" that Nautilus would show up as would be a very different color from the "windows" that Gnome File Manager opens. Same for GEdit when it's running under Alt-F2 (gksudo) and the non-root-user "window".

All too often I have multiple iterations of the file manager windows open and I can't tell which is under sudo and which is 'user'.

Thanks for your time.

---

### Post by -grubby on 2008-10-28
Thunar alerts you when it is running under root

---

### Post by urukrama on 2008-10-28
Just create a custom .gtkrc-2.0 file in /root. Here is what you would put in there:

> include "/path/to/your/preferred/themes/gtkrc/file"

gtk-icon-theme-name = "iconthemename"



---

### Post by jpeddicord on 2008-10-28
This is what I use:

Open a root Nautilus (gksu nautilus) and go to Edit > Backgrounds and Emblems. Click colors, and find a nice bright-red color. Click and drag it onto the background of the Nautilus window, and it will turn red. This will only apply to the rooted Nautilus and not your local account.

Same for Gedit, but just change the color scheme to Oblivion in Edit > Preferences. The inverted screen is a good hint for root mode.

(Also, moved to Desktop Environments.)

---

### Post by Mark_in_Hollywood on 2008-10-29
> **jacobmp92 said:**
> This is what I use:

Open a root Nautilus (gksu nautilus) and go to Edit > Backgrounds and Emblems. Click colors, and find a nice bright-red color. Click and drag it onto the background of the Nautilus window, and it will turn red. This will only apply to the rooted Nautilus and not your local account.

Same for Gedit, but just change the color scheme to Oblivion in Edit > Preferences. The inverted screen is a good hint for root mode.

(Also, moved to Desktop Environments.)

While this works to alert a user of which gedit or file manager is in use, it is the exact opposite of what I want. I want to change the frame color of gedit or nautilus. So instead of Ubuntu "brown" and the text gedit / home and such, I want the background color and the text color to clearly show that the user is /

Thanks, your way is better than no way.

---

