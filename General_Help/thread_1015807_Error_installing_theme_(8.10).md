---
title: "Error installing theme (8.10)"
date: 2008-12-19
forum: General Help
---

### Post by ckth on 2008-12-19
Hello,

I'm having trouble installing the [Glow Ibex]("http://www.gnome-look.org/content/show.php/Glow+Ibex?content=87514") theme in Ubuntu 8.10.

I have the requisite theme engines installed (Aurora, Clearlooks, Pixmap, and a few more, Glow Ibex only requires Aurora and Clearlooks).

There are two problems with installing a theme:

1. When I drop the .tar.gz file into the Appearances window, it installs the theme (that is, extracts and copies to ~/.themes) just fine. But when I apply the theme, I get a message saying: 

```
This theme will not look as intended because the GTK+ theme "Glow Ibex" is not installed.
```

And that's immediately *after* I installed it!
Then some attributes of the theme, like the window background color, are applied while most attributes (borders, buttons, fonts) are not.

2. The Glow Ibex theme does not show up in the themes window at all, meaning that I cannot use the (broken) theme except when I install it. A few others seem to be having this problem on 8.10 right now, so I can wait for this to be sorted out.

Any help is appreciated.

---

### Post by Ivo Moelans on 2008-12-19
1) You probably have a defective gtkrc file in the theme (I downloaded mine from *[http://www.gnome-look.org/content/show.php/Glow+Ibex?content=87514]("http://www.gnome-look.org/content/show.php/Glow+Ibex?content=87514")* and that works fine).
Download the attached file, unpack it and copy it over the one in */home/<username>/.themes/Glow Ibex/gtk-2.0/*

2) The theme lacks an *index.theme* file. Open Text Editor (*Applications&#8594;accessories&#8594;Text Editor*) and insert this code:

```
[Desktop Entry]
Version=0.0.1
Encoding=UTF-8
Name=Glow Ibex
Type=X-GNOME-Metatheme
Comment=Something

[X-GNOME-Metatheme]
GtkTheme=Glow Ibex
MetacityTheme=Glow Ibex
IconTheme=<insert here name of icon theme you want to use>
CursorTheme=<insert here name of cursor theme you want to use>
CursorSize=18
```

Change the *IconTheme* and *CursorTheme* entries with your preferred themes.
Save the file as *index.theme*. It will rename itself to *Glow Ibex*. Put this file in */home/<username>/.themes/Glow Ibex*.

Now you should see Glow Ibex in the Appearance Preferences main window.

Hope this helps

---

