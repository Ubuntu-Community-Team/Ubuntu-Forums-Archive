---
title: "Looking for info on making a theme."
date: 2012-06-08
forum: Desktop Environments
---

### Post by ferulebezel on 2012-06-08
I'm trying to make some new themes.  Unfortunately I can't find any information via google.  Perhaps I suck an coming up with search terms.

What I'm looking for is an explanation of the *.css files.  There seems to be features in them that goes beyond what I've learned messing around with web pages.  

I don't understand the things like:
```

color: shade (@bg_color, 0.6);
text-shadow: 0 1 alpha (shade (@bg_color, 1.25), 0.5)
```

what are these -unico values?

And in lines like:
```

GtkComboBox.combobox-entry .button,
.button:active,
.button:insensitive{

```

are all buttons, active buttons and insensitive buttons affected by what is within the curly braces or is it just the ones within a combobox.

What I also would like is a picture of the components (I believe the term might be "widgets") labeled with what they are called in the files.

Are these files documented anywhere?

---

### Post by LarsKongo on 2012-06-08
**shade** is what it sounds like. The shade of the color value @bg_color (that's defined in the gtk.css file.) The lower the value the darker the color gets and vice versa.

**alpha** is the transparency of the color. 0.0 is invisible. 1.0 is fully visible.

**:active** (or in some cases **:selected**) is the pressed/selected state of something. So for example: *.button:active { background-color: shade (@bg_color, 0.6); }* will make all buttons darker when they're pressed.

**:insensitive** is the state of items you can't interact with. (A grayed out button for example.)

**-unico* values** are engine specific settings for the Unico GTK3 engine.

AWF is useful when testing any changes you do to a theme: [https://github.com/valr/awf](https://github.com/valr/awf) (It doesn't update in real time though, so you'll need to close the gtk3 part of the app and open it again to test any changes.)

---

### Post by cortman on 2012-06-08
Are you talking about themes for Gnome shell?

If so, it's pretty easy- I've done one myself, and would like to do more if I can find time.
With CSS, the best way to learn is just to play with it. Install a theme, open up the existing CSS file in ~/.themes/theme_name, and start changing things. Change a value or two, save, and run "r" in the Alt+F2 box to restart the desktop. See if it changed.
As clunky as that sounds that was the best way I learned it. Just have fun with tweaking things. :)

---

### Post by Frogs Hair on 2012-06-08
Lots of information here . [http://developer.gnome.org/gtk3/3.0/](http://developer.gnome.org/gtk3/3.0/)

---

### Post by ferulebezel on 2012-06-19
I've gotten pretty far but still have some problems.

I can't figure out what is the variable for the color of the box and shading you get when resizing a window or the area surrounding the buttons on the title bar in a non maximized window.  

What kind of ineritance mechanism is there?  GtkCombobox.button inherit the values for .button?

Finally, I beg again.  Has anyone compiled a list of the variaiables, preferably with a picture of the components they control.

---

