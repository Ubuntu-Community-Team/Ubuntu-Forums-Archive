---
title: "changing font color of the &quot;Switch user&quot; applet"
date: 2008-12-22
forum: General Help
---

### Post by LinuxFanBoi on 2008-12-22
I've customized everything on my gnome panel but can not seem to figure out how to change the font color for the "switch User" applet that by default runs in the upper right corner of the screen on a fresh Ubuntu install.

this is a crop of what I want to change, please direct your attention to the lower right of the image:
[IMG]http://i450.photobucket.com/albums/qq221/Xtrasmall_photos/Screenshot.png[/IMG]

this is the code in my config file:
```
style "panel"
{
  fg[NORMAL]               = "#ffffff"#panel txt normal
  fg[PRELIGHT]            = "#ffffff"
  fg[ACTIVE]               = "#ffffff"
  fg[SELECTED]            = "#ffffff"
  fg[INSENSITIVE]            = "#ffffff"
  bg[NORMAL]               = "#85897F" #Background of switcher and wl fine outline
  bg[PRELIGHT]            = "#000000"#Mouseover wl
  bg[ACTIVE]               = "#000000"#Selected wl
  bg[SELECTED]            = "#000000"#Mouseover outline
  bg[INSENSITIVE]            = "#FAFF00"#??
 base[NORMAL]            = "#5D605A"#Background of things like deskbar or 'add to panel'
  base[PRELIGHT]            = "#ffffff"#fine outline on windowlist items
  base[ACTIVE]            = "#ffffff"
  base[SELECTED]            = "#ffffff"
  base[INSENSITIVE]         = "#ffffff"

  text[NORMAL]            = "#ffffff"
  text[PRELIGHT]            = "#000000"
  text[ACTIVE]               = "#000000"
  text[SELECTED]            = "#ffffff"
  #text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
```

Can anyone point me to the line I need to edit or what line I need to add in order to achive the changes I am looking for?

---

### Post by IamReck on 2008-12-22
I had a similar problem, my workaround was just to right-click on the icon, select Preferences and Under Appearance just make it the picture of the person.  That way there is no Text there at all, it also takes up less space.

---

### Post by LinuxFanBoi on 2008-12-22
Novel idea, but not what I'm looking for... thanks for the thought though =P

---

### Post by IceReaver75 on 2008-12-22
I'm not sure but by looking at a gktrc file that I have here I would try to change either one of these 2 lines

text[PRELIGHT]            = "#000000"
text[ACTIVE]               = "#000000"

to make it a white color which by the rest of the theme text colors would be the "ffffff"

---

### Post by LinuxFanBoi on 2008-12-23
tried both of those lines... no luck.. any other ideas?

---

### Post by LinuxFanBoi on 2008-12-23
bump

---

### Post by Ivo Moelans on 2008-12-23
You could try this:

```
############# Fast User Switch Applet ############################
style "fus" = "panel"
{
	fg[NORMAL] 		= "#FF0000"
}
widget "*fast-user-switch*" 		style "fus"
```

Place this code in */home/<username>/.themes/NameOfTheme/gtk-2.0/panel.rc*. It could be that the file is called *panelrc*. It is critical where this code is placed in the file because there is a certain sequence involved. I don't know precisely just where to put it, but it is more likely to be at the beginning of the file. You'll have to experiment a bit.
I've used red in the code, but of course you can put there whatever color you like. Use *Applications&#8594;Graphics&#8594;Gcolor2*. You can install it with *Synaptic Package Manager* if it's not already installed. (White = "#FFFFFF")
Let me know how it goes

---

### Post by LinuxFanBoi on 2008-12-24
the folder /.themes is empty within my home folder.

---

### Post by Ivo Moelans on 2008-12-24
Try */usr/share/themes*. You'll need superuser privileges to modify a file (terminal: *gksudo gedit*).

---

### Post by Ivo Moelans on 2008-12-24
Alternative:
Create a simple text file with Text Editor. Copy & paste the code. Save is as *.gtkrc-2.0* (don't forget the ".") in your home directory. Logout & login.
The disadvantage is that it will then always apply, regardless of which theme you're using.

---

