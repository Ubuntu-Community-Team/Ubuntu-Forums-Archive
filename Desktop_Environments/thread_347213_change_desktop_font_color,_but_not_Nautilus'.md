---
title: "change desktop font color, but not Nautilus'"
date: 2007-01-26
forum: Desktop Environments
---

### Post by munkar on 2007-01-26
hi, people who know about .gtkrc-2.0!

i downloaded a darker desktop wallpaper, and noticed that all of my desktop fonts were black and almost unreadable. so i figured out that i have to make a .gtkrc-2.0 file like this:

```
style "desktop-icon"
{
NautilusIconContainer::normal_alpha = 0 
text[NORMAL] = "#ffffff" 
NautilusIconContainer::frame_text = 1 
}
class "GtkWidget" style "desktop-icon"
```

right? but the problem is, if i do this, the desktop colour turns to white very nicely, but so does the colour of the font in Nautilus' file browser, making the file and folder names disappear against the white background!

how do i make the desktop font white, but the file browser font black?!

---

### Post by tweedledee on 2007-01-27
> **munkar said:**
> how do i make the desktop font white, but the file browser font black?!

I haven't played with themes enough to answer your question, but the solution in this thread may help (gnome-color-chooser, there is a .deb attachment): [http://www.ubuntuforums.org/showthread.php?t=293342](http://www.ubuntuforums.org/showthread.php?t=293342)

---

### Post by ComplexNumber on 2007-01-27
or you could just use [this]("http://gnome-look.org/content/show.php?content=47349").

---

### Post by munkar on 2007-01-28
aha! found the answer in [this thread]("http://www.ubuntuforums.org/showthread.php?t=89197&page=4&highlight=nautilus+font+color"). the correct file contents are:

```
style "desktop-icon" {
     NautilusIconContainer::frame_text = 1
      text[NORMAL] = "#FFFFFF"
     NautilusIconContainer::normal_alpha = 44
}
#class "GtkWidget" style "desktop-icon"
widget_class "*DesktopIcon*" style "desktop-icon"
```

---

