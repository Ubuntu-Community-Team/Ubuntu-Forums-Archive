---
title: "default teminal window size"
date: 2005-09-10
forum: Desktop Environments
---

### Post by doc_holiday on 2005-09-10
Hey,

I'm using gnome and would like the change the default size of the terminal window.
Is there a way to do this?

thanks
Doc

---

### Post by gjaffe on 2005-09-10
Do you mean increase the font size and keep the same number of characters per line and lines per page?  Or do you mean keep the font size the same and increase the number of lines or characters?

The first is easy.  

You click on Edit->Current Profile in the menu bar.  That will open up an "Edit Profile" window.  Simply change the font to something larger.

If you want to change the number of characters per line or number of lines per page, that is done with the --geometry option on the command line.  The easiest way to do this (that I know) is to place a launcher for the gnome-terminal in your panel.  Find Applications->System Tools->Terminal in the gnome menu.  Right click on it and choose "Add this launcher to panel".

Once you have the launcher in your panel, right click on it and select Properties.  In the new window change the Command from "gnome-terminal" to "gnome-terminal --geometry 80x30".  Then click on the Close button.  That will cause it to launch a terminal that is 80 characters by 30 lines each time.  Edit the numbers to suit your needs.

Gary

---

### Post by doc_holiday on 2005-09-10
[QUOTE=gjaffe] "gnome-terminal --geometry 80x30".  

Gary[/QUOTE]
This is wat I needed, thank you

---

