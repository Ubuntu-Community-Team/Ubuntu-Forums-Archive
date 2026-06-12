---
title: "Active window color in the panel"
date: 2008-12-22
forum: General Help
---

### Post by davidself1001 on 2008-12-22
Is there a way to change the color of the active window panel (ie the one that is highlighted when active in the Gnome panel)?  You can change the panel background color but it doesn't affect the active window panels color.  In general where are the Gnome panel attributes saved?

---

### Post by davidself1001 on 2008-12-22
Found some earlier threads that indicated that the file .gtkrc-2.0 is used for modifying the panel attributes.  Does anyone know where this file needs to reside?

---

### Post by IceReaver75 on 2008-12-22
The gtkrc file for the theme is in the gtk-2.0 folder of the theme itself.  The theme folders are usually found in the .themes folder in you home folder(have to hit ctrl-h to see hidden folders) or the /usr/share/themes folder. You can open the gtkrc file with a text editor and make the changes you need.  It will make a backup itself usually when you edit it so if you change something and its not right you can replace it with the backup.  Hope that helps some.

---

### Post by davidself1001 on 2008-12-22
bump

---

### Post by davidself1001 on 2008-12-22
That helped.  There are many themes (i have downloaded) in both the .themes dir as well as the usr/share/themes dir.  These seem to be the metacity themes that I have downloaded.  The one I have selected says custom because I have made some changes to it.  How do I know which theme is active (ie which gtkrc file do I need to edit?

---

### Post by IceReaver75 on 2008-12-22
If you go back to the apperance setting and click customize on the theme your using the one highlighted under the controls tab is the gtk theme your custom theme is using right now.

When you open the gtk-2.0 file for the theme there usually is a panel folder in there.  To change the color of the active panel buttons you are going to want to change the color of the panel-buttons and panel menubar files using gimp or other graphics program.  The gtkrc file usually just tells the theme where to pull the files from and usually text colors of everything.

---

### Post by davidself1001 on 2008-12-22
Ok, still not working.  I selected a specific theme, went to that dir /usr/share/themes/selected theme/.gtk-2.0 and edited the gtkrc file (various different color items).  Did not affect the panel.  I am editing the following section of the file:

#default color scheme
gtk_color_scheme = "fg_color:#000000\nbg_color:#d4d4d4\nbase_color:#ffffff\ntext_color:#000000\nselected_bg_color:#0c83c8\nselected_fg_color:#ffffff"

I've changed various values with no affect.  I also need to note that I am using Emerald for window decoration.  Does that impact the gnome panel colors, etc?

---

